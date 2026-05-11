---
name: opairview-mini
description: Save, organize, and search research links. Triggers automatically when user sends only a URL. Also use for finding saved links, listing collections, or deleting links. Fully on-device — no cloud required.
metadata:
  version: "1.1"
  author: OPAIRS systems FlexCo
  homepage: https://opairs-systems.com/insights/opairs-pipeline-von-daten-zu-entscheidungen
---

# OPAIRview mini

A personal knowledge base for saving and organizing research links — fully on-device, no cloud required.

## Instructions

### Auto-save — URL only (most important trigger)
When the user sends ONLY a URL (e.g. `https://example.com/article`) with no other instruction, immediately save it without asking. Infer the title from the domain/path and the collection from the URL content.

Call `run_js` with:
- script name: `index.html`
- data: `{"action":"save","url":"<url>","title":"<inferred>","collection":"<inferred>","notes":"","tags":[]}`

### Save a link with metadata
When the user saves a URL with explicit details:
- script name: `index.html`
- data fields:
  - `action`: `"save"` (required)
  - `url`: The URL (required)
  - `title`: Short descriptive title — infer from URL path if not given (required)
  - `collection`: Topic e.g. `"EU AI Act"`, `"Wettbewerb"`, `"Kunden"`, `"Tech"`, `"Förderung"` (required)
  - `notes`: Optional key takeaway or annotation
  - `tags`: Optional keyword array e.g. `["DSGVO","KI","compliance"]`

Example: `{"action":"save","url":"https://example.com/eu-ai","title":"EU AI Act Übersicht","collection":"EU AI Act","notes":"Anforderungen für KMU","tags":["compliance","DSGVO"]}`

### Search links
- script name: `index.html`
- data: `{"action":"search","query":"<terms>"}`

Searches across: title, URL, domain, collection, notes, tags, and date (DD.MM.YYYY).

### List collections or links
All collections: `{"action":"list"}`
Links in a collection: `{"action":"list","collection":"<name>"}`

### Delete a single link
Get ID via search/list first: `{"action":"delete","id":"<id>"}`

### Delete all links in a collection
`{"action":"clear_collection","collection":"<name>"}`

## Response guidelines
- **URL only → save immediately, no questions**
- After saving: one line — title, collection, tags, date
- After searching: title + URL + tags + date, title matches first
- After listing: collections with counts, or links with metadata
- Concise responses only
- Tool returns German; respond in user's language
