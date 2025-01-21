---
title: "FHIR JSON Schemas for VS Code and Zed"
date: 2025-01-03T14:00:00
lastmod: 2025-01-21T12:00:00
draft: false
tags:
  - FHIR
  - Code
summary: "Getting better code completion and validation for FHIR resources in VS Code and Zed for those stubborn people who still write JSON by hand."
aliases:
  - /blogs/fhir-schema-vs_code/
---

_Update on 2025-01-21 to add configuration for [Zed](https://zed.dev/)_

I often create proof-of-concept FHIR resources by hand in VS Code&mdash;especially for terminological resources, creating a simple resource is often faster than using SUSHI, my own [BabelFSH](https://mii-termserv.de/en/tools/babelfsh/) tool, or something else entirely, but a bit of assistance would be helpful.

Turns out you can add JSON schemas to VS code _and Zed_ to get better code completion and validation for FHIR resources. Downloading the JSON schemas from the FHIR spec is easy enough, but how to put them into VS Code? That's where this website comes in. By uploading the schema files to the page, I get a convenient download link, so that I can simply point VS code _or Zed_ there.

Since I mainly need the FHIR R4 schemas, I have made those the default. Adjust as needed. Happy hacking!

## VS Code Setup

Open the user settings in JSON format using the _Preferences: Open User Settings (JSON)_ command (this could of course also be done in the workspace settings) and add something like the following:

```json
{
  "json.schemas": [
    {
      "fileMatch": ["*.fhir.json*", "*.fhir-r4.json*"],
      "url": "https://wiedekopf.net/data/fhir-r4.schema.json"
    },
    {
      "fileMatch": ["*.fhir-r4b.json"],
      "url": "https://wiedekopf.net/data/fhir-r4b.schema.json"
    },
    {
      "fileMatch": ["*.fhir-r5.json"],
      "url": "https://wiedekopf.net/data/fhir-r5.schema.json"
    }
  ]
}
```

[[Source]](https://code.visualstudio.com/docs/languages/json#_json-schemas-and-settings)

## Zed setup

[Zed](https://zed.dev/) is configured in a JSON file, either on a global or a per-project level.

For the global settings, open the settings file using the `zed: open settings` action, and add a section like the following:

```json
{
  // snip
  "lsp": {
    "json-language-server": {
      "settings": {
        "json": {
          "schemas": [
            {
              "fileMatch": ["*/*.fhir.json*", "*/*.fhir-r4.json*"],
              "url": "https://wiedekopf.net/data/fhir-r4.schema.json"
            },
            {
              "fileMatch": ["*/*.fhir-r4b.json"],
              "url": "https://wiedekopf.net/data/fhir-r4b.schema.json"
            },
            {
              "fileMatch": ["*/*.fhir-r5.json"],
              "url": "https://wiedekopf.net/data/fhir-r5.schema.json"
            }
          ]
        }
      }
    }
  }
}
```

[[Source]](https://zed.dev/docs/languages/json)

## URIs

For reference: The following files are currently hosted at this site:

- {{< code-link href="https://wiedekopf.net/data/fhir-r4.schema.json" >}}
- {{< code-link href="https://wiedekopf.net/data/fhir-r4b.schema.json" >}}
- {{< code-link href="https://wiedekopf.net/data/fhir-r5.schema.json" >}}
