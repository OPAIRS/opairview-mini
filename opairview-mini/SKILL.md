---
name: opairview-mini
description: Save, organize, and search research links in topic collections. Use when the user wants to save a URL, find saved links, list collections, browse research materials, or delete a saved link. Fully on-device — no cloud required.
metadata:
  version: "1.0"
  author: OPAIRS systems FlexCo
  homepage: https://opairs-systems.com/insights/opairs-pipeline-von-daten-zu-entscheidungen
---

# OPAIRview mini

A personal knowledge base for saving and organizing research links in topic collections — fully on-device, offline-capable, no cloud required.

## Instructions

### Save a link
When the user wants to save a URL or link, call the `run_js` tool with:
- script name: `index.html`
- data: A JSON string with the following fields:
  - `action`: `"save"` (required)
  - `url`: The URL to save (required)
  - `title`: A short descriptive title — infer from context if not provided by the user (required)
  - `collection`: Topic category such as `"EU AI Act"`, `"Wettbewerb"`, `"Kunden"`, `"Tech"`, `"Förderung"` — infer from context or ask the user (required)
  - `notes`: Optional short annotation, key takeaway, or summary of why this link is relevant

Example data: `{"action":"save","url":"https://example.com/article","title":"EU AI Act Übersicht","collection":"EU AI Act","notes":"Gute Zusammenfassung der Anforderungen"}`

### Search links
When the user wants to find, search, or look up saved links, call `run_js` with:
- script name: `index.html`
- data: `{"action":"search","query":"<search terms>"}`

### List collections or browse links
When the user wants to see an overview of all collections, call `run_js` with:
- script name: `index.html`
- data: `{"action":"list"}`

When the user wants to see all links in a specific collection, call `run_js` with:
- script name: `index.html`
- data: `{"action":"list","collection":"<collection name>"}`

### Delete a single link
First search or list links to identify the link's ID. Then call `run_js` with:
- script name: `index.html`
- data: `{"action":"delete","id":"<link id>"}`

### Delete all links in a collection
Call `run_js` with:
- script name: `index.html`
- data: `{"action":"clear_collection","collection":"<collection name>"}`

## Response guidelines
- After saving: confirm what was saved and in which collection
- After searching: present results clearly with title, URL, and notes
- After listing without collection: show all collections with their link counts
- After listing with collection: show all links in that collection
- After deleting: confirm what was removed
- Keep responses concise — this is a personal assistant, not a verbose system
- The tool returns German text; respond in the user's preferred language
