# Workflow Notes

## Workflow Purpose

This n8n workflow generates structured real estate content packs from Google Sheets briefs using the OpenAI API.

The workflow supports two main request modes:

- `initial`
- `regenerate`

The goal is to create a reusable automation system that can generate, revise, validate and prepare content for human review and future export.

## High-Level Flow

1. Read content requests from Google Sheets
2. Normalize the input fields
3. Validate required fields
4. Route the request based on `request_mode`
5. Generate or regenerate content using the OpenAI API
6. Parse the AI response into structured fields
7. Save the output into Google Sheets
8. Log invalid requests into the Errors tab
9. Keep content ready for review and future export

## Input Layer

The workflow starts by reading rows from Google Sheets.

Each row contains a structured content brief with fields such as:

- `request_mode`
- `content_type`
- `platform`
- `goal`
- `idea_seed`
- `target_client`
- `suburb`
- `property_type`
- `key_facts`
- `brand_voice`
- `offer_angle`
- `compliance_note`
- `feedback`
- `generated_caption`

## Request Modes

## Initial Mode

The `initial` branch creates a new content pack from the original brief.

Required fields include:

- `goal`
- `idea_seed`
- `key_facts`

If those fields are present, the workflow sends the brief to the OpenAI API and generates a structured content pack.

## Regenerate Mode

The `regenerate` branch revises an existing draft using human feedback.

Required fields include:

- `goal`
- `idea_seed`
- `key_facts`
- `feedback`
- `generated_caption`

If the required fields are present, the workflow sends the original brief, current draft and feedback to the OpenAI API to create an improved version.

## Validation Logic

The workflow includes basic validation before generating or regenerating content.

Invalid rows are not processed as valid content requests.

Instead, they are logged into the `Errors` tab.

This prevents incomplete rows from being treated as successful content generation requests.

## Error Handling

The workflow logs invalid requests when required fields are missing.

Examples of invalid scenarios:

- missing `goal`
- missing `idea_seed`
- missing `key_facts`
- missing `feedback` in regenerate mode
- missing `generated_caption` in regenerate mode

A future improvement would be to make the Errors tab more detailed by adding extra diagnostic fields such as:

- `feedback`
- `generated_caption`
- `request_mode`
- `error_reason`
- `timestamp`

## OpenAI API Calls

The workflow uses two OpenAI HTTP Request nodes:

- one for initial content generation
- one for regeneration with feedback

Both nodes use structured prompts that ask the model to return content using fixed section headers.

## Generated Content Fields

The AI response is parsed into the following output fields:

- `hooks`
- `script`
- `visual_structure`
- `on_screen_text`
- `camera_angle`
- `b_roll_idea`
- `text_overlay_priority`
- `editing_note`
- `generated_caption`
- `cta`
- `hashtags`

## Video-Ready Fields

The workflow includes video-ready fields to make the output more useful for Reel production.

These fields are:

- `camera_angle`
- `b_roll_idea`
- `text_overlay_priority`
- `editing_note`

These fields help guide filming, supporting footage, text hierarchy and editing direction.

## Parsing Logic

The AI response is returned as structured text with fixed section labels.

The workflow uses Edit Fields nodes to extract each section and save it as a separate field.

The parsing logic was adjusted to prevent fields such as `ON_SCREEN_TEXT` and `CTA` from being mixed with nearby sections.

## API Reliability

Basic retry logic was added to both OpenAI API request nodes.

Current configuration:

- Retry on Fail: enabled
- Max tries: 3
- Wait between tries: 3000 ms

This provides basic protection against temporary API failures or rate-limit issues.

Loop Over Items + Wait was reviewed but not implemented in this MVP because the workflow does not currently process large batches of rows.

For future bulk generation, the workflow could process rows sequentially and add a short delay between API calls.

## Output Layer

Generated and regenerated content is saved into Google Sheets.

The output structure is designed to support:

- human review
- feedback
- approval status
- testing
- future export
- future publishing integration

## Review Logic

The workflow supports review statuses such as:

- `draft`
- `review`
- `approved`
- `rejected`
- `exported`

Regenerated content is saved with a review-oriented status because it still needs human approval before being exported or published.

## Current Limitations

The current workflow does not include:

- direct social media publishing
- direct CRM integration
- automatic image generation
- automatic video editing
- advanced analytics
- automatic trend detection
- detailed API failure logging after retry attempts

## Future Improvements

Possible technical improvements:

- add bulk processing with Loop Over Items + Wait
- improve the Errors tab with more diagnostic fields
- export a safe version of the n8n workflow JSON
- add CSV export for scheduling tools
- add image generation
- add story and carousel generation
- add analytics feedback loop
- connect the workflow to a CRM or content scheduler
