# OPAIRview mini – Edge Gallery Skill

A personal knowledge base skill for [Google AI Edge Gallery](https://github.com/google-ai-edge/gallery).

Save research links with metadata, organize them into topic collections, and search them — fully on-device, no cloud, no SaaS.

## What it does

| Command | Example |
|---|---|
| Save a link | *"Speichere https://example.com unter EU AI Act"* |
| Search links | *"Suche nach Datenschutz"* |
| List collections | *"Zeig mir alle Collections"* |
| Browse a collection | *"Zeig alle Links unter Wettbewerb"* |
| Delete a link | *"Lösch den Link mit ID 1234567890"* |
| Clear a collection | *"Lösch alle Links aus Förderung"* |

## Install

### Option A – Load from URL via GitHub Pages (empfohlen für JS Skills)
> ⚠️ `raw.githubusercontent.com` funktioniert **nicht** für JS Skills — falscher MIME-Type für den Webview. GitHub Pages verwenden.

1. GitHub Pages aktivieren: Repo → Settings → Pages → Branch: `main`, Folder: `/root`
2. Warten bis Pages aktiv ist (ca. 1 Min.)
3. In Edge Gallery → Agent Skills → Skill Manager → `+` → **Load skill from URL**
4. URL eingeben: `https://<your-username>.github.io/opairview-mini/opairview-mini/`

Prüfen ob bereit: `https://<your-username>.github.io/opairview-mini/opairview-mini/SKILL.md` im Browser öffnen — raw Markdown muss erscheinen.

### Option B – Load from device (für schnelles Testen)
```bash
adb push opairs-research-hub/ /sdcard/Download/opairs-research-hub
```
Dann in Edge Gallery → Skill Manager → `+` → **Import local skill** → Ordner auswählen.

## Repo structure

```
opairs-research-hub/          ← skill directory
├── SKILL.md                  ← skill definition + LLM instructions
└── scripts/
    └── index.html            ← JS logic (webview), localStorage persistence
```

## Requirements
- Google AI Edge Gallery app (Android 12+ or iOS 17+)
- Gemma 4 E2B or E4B model downloaded in the app

## Development
Developed by [OPAIRS systems FlexCo](https://opairs-systems.com) — On-Premise AI Orchestration for Manufacturing.

Contributions and extensions welcome. Continue development with Claude Code.

## License
Apache 2.0
