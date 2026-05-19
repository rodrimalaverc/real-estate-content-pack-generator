# Project Overview

## Project Name

Real Estate Content Pack Generator

## Summary

The Real Estate Content Pack Generator is an AI automation MVP built with n8n, Google Sheets and the OpenAI API.

The system receives structured real estate content briefs from Google Sheets, validates the required fields, generates structured content packs, supports regeneration with human feedback, logs invalid requests and prepares the content for review and future export.

## Problem

Real estate businesses often need regular content for social media, but the process can be manual, inconsistent and difficult to scale.

Common problems include:

- Content ideas are not always structured
- Captions and scripts are created manually
- Feedback is not captured in a clear workflow
- Content approval is not always organised
- Outputs are not always prepared for future publishing
- Repetitive content tasks take too much time

## Solution

This MVP creates a structured AI-assisted content workflow.

Instead of generating random captions, the workflow uses a content brief and produces a complete content pack with:

- hooks
- script
- visual structure
- on-screen text
- caption
- CTA
- hashtags
- video-ready production notes

The system also includes review statuses, regeneration with feedback, validation rules, error logging and testing documentation.

## Main Use Case

A real estate business can use this workflow to create content ideas and draft social media assets faster while keeping a human review process.

Example use cases:

- listing reels
- suburb guides
- market updates
- first-home buyer tips
- seller objection content

## Business Value

The workflow helps a business:

- reduce manual content creation time
- create more consistent content outputs
- structure feedback and revisions
- keep content aligned with business goals
- prepare content for review and future publishing
- build a reusable content operations process

## MVP Scope

This version focuses on workflow logic and structured text generation.

Included in the MVP:

- Google Sheets input and output structure
- initial content generation
- regeneration with feedback
- required field validation
- error logging
- review statuses
- video-ready output fields
- testing matrix
- retry logic for API reliability
- export-ready structure

Not included in this MVP:

- direct social media publishing
- direct CRM integration
- automatic image generation
- automatic video editing
- automatic trend scraping
- advanced analytics

## Tech Stack

- n8n
- Google Sheets
- OpenAI API
- GitHub

## Current Status

The MVP is functional and documented as a portfolio project.

Completed:

- workflow built in n8n
- initial and regenerate branches completed
- validation and error logging implemented
- video-ready fields added
- 10 structured tests completed
- screenshots uploaded
- GitHub documentation in progress

## Future Roadmap

Possible phase 2 improvements:

- add direct publishing or scheduling integration
- add image generation
- add story and carousel generation
- add a strategy-driven content planner
- add stronger error reporting
- add analytics and performance tracking
- add a CSV export for bulk scheduling
- add CRM or external platform integration
