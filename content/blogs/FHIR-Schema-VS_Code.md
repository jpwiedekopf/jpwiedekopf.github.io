---
title: "FHIR JSON Schemas for VS Code"
date: 2025-01-03T14:00:00
draft: false
github_link: "https://github.com/gurusabarish/hugo-profile"
tags:
  - FHIR
  - Code
summary: "Getting better code completion and validation for FHIR resources in VS Code for those stubborn people who still write JSON by hand."
---

I often create proof-of-concept FHIR resources by hand in VS Code&mdash;especially for terminological resources, creating a simple resource is often faster than using SUSHI, my own [BabelFSH](https://mii-termserv.de/en/tools/babelfsh/) tool, or something else entirely, but a bit of assistance would be helpful.

Turns out you can add JSON schemas to VS code to get better code completion and validation for FHIR resources. Downloading the JSON schemas from the FHIR spec is easy enough, but how to put them into VS Code? That's where this website comes in. By uploading the schema files to the page, I get a convenient download link, so that I can simply point VS code there.

Open the user settings in JSON format using the *Preferences: Open User Settings (JSON)* command (this could of course also be done in the workspace settings) and add something like the following:

{{< highlight json >}}
{
    "json.schemas": [
        {
            "fileMatch": [
                "*.fhir.json*",
                "*.fhir-r4.json*"
            ],
            "url": "https://wiedekopf.net/data/fhir-r4.schema.json"
        },
        {
            "fileMatch": [
                "*.fhir-r4b.json",
            ],
            "url": "https://wiedekopf.net/data/fhir-r4b.schema.json"
        },
        {
            "fileMatch": [
                "*.fhir-r5.json",
            ],
            "url": "https://wiedekopf.net/data/fhir-r5.schema.json"
        }
    ],
}
{{< /highlight >}}

Since I mainly need the FHIR R4 schemas, I have made those the default. Adjust as needed. Happy hacking!

---

For reference: The following files are currently hosted at this site:
- `https://wiedekopf.net/data/fhir-r4.schema.json`
- `https://wiedekopf.net/data/fhir-r4b.schema.json`
- `https://wiedekopf.net/data/fhir-r5.schema.json`