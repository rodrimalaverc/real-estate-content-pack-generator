# Screenshots

This folder contains visual evidence of the Real Estate Content Pack Generator MVP.

The screenshots show the main workflow architecture, the Google Sheets structure, generated outputs, review logic, testing matrix and error handling examples.

## Screenshot list

### 01-workflow-overview.png

High-level view of the n8n workflow.

It shows the main workflow structure, including:
- input layer
- required field validation
- request mode router
- initial content generation
- regeneration with feedback
- output and review layer
- error logging path

### 02-google-sheets-structure.png

Overview of the Google Sheets structure used as the operational layer of the MVP.

The spreadsheet includes tabs for:
- content requests
- generated outputs
- review
- errors
- export
- idea bank
- preset library
- testing matrix

### 03-generated-output-example.png

Example of an AI-generated real estate content pack.

The output includes:
- hooks
- script
- visual structure
- on-screen text
- caption
- CTA
- hashtags
- video-ready fields such as camera angle, B-roll idea, text overlay priority and editing note

### 04-review-flow-example.png

Example of the human review layer.

This screenshot shows how generated content can be reviewed using statuses such as:
- draft
- review
- approved
- rejected
- exported

### 05-testing-matrix.png

Testing matrix created for the MVP.

The test cases cover:
- valid initial generation
- missing required fields
- valid regeneration
- missing feedback
- missing previous draft
- validation of video-ready fields
- field separation checks

### 06-error-handling-example.png

Example of the validation and error handling structure.

This shows how invalid requests can be logged instead of being treated as valid content generation requests.
