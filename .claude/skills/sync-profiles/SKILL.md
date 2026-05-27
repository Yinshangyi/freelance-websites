---
name: sync-profiles
description: Use when updating freelance platform profiles (LinkedIn, Malt, Free-Work, Comet, Collective) from local source of truth files. Trigger on "sync profiles", "update profiles", "update LinkedIn/Malt/Freework", or any request to push profile content to freelancing platforms.
---

# Sync Freelance Profiles

Update one or more freelancing platform profiles from the local markdown source of truth.

## Source of Truth

Local files in the `freelance-websites` repo at `/Users/jean-loicdejaeger/Documents/freelance-websites/profile/`:

```
profile/
├── en/           # English content
│   ├── about.md
│   ├── experiences.md
│   ├── education.md
│   └── certifications.md
└── fr/           # French content
    ├── about.md
    ├── experiences.md
    ├── education.md
    └── certifications.md
```

## Platforms

| Platform | Language | URL | Tool |
|----------|----------|-----|------|
| LinkedIn | EN | https://www.linkedin.com/in/jean-loic-de-jaeger-developer-java-kotlin/ | LinkedIn MCP |
| Free-Work (FR) | FR | https://www.free-work.com/fr/resume | Playwright MCP |
| Free-Work (EN) | EN | https://www.free-work.com/en-gb/resume | Playwright MCP |
| Collective | FR | https://app.collective.work/collective/jeanloic-de-jaeger/profile | Playwright MCP |
| Malt | FR | https://www.malt.fr/profile/jeanloicdejaeger | Playwright MCP |
| Comet | FR | https://app.comet.co/freelancer/profile | Playwright MCP |

## Workflow

1. Ask the user which platform(s) to update, or update all if requested.
2. Read the relevant source files (`en/` or `fr/` based on platform language).
3. For **LinkedIn**: use the LinkedIn MCP tools to edit the profile directly.
4. For **all other platforms**: use the Playwright MCP to navigate to the profile URL and update fields.
5. Update each section one by one: About, Experiences, Education, Certifications.

## Rules

- Platform content must **exactly match** the source files — nothing more, nothing less.
- Remove any content on the platform that is not in the source files.
- Skip fields that don't exist on the platform.
- Use `fr/` folder for French platforms, `en/` folder for English platforms.
