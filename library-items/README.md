# Library Items — Pre-Made Knowledge Entries
*Production-tested patterns ready to install into your library*

## What Are Library Items?

Pre-made knowledge entries following Library System's format templates. Install proven patterns instantly instead of building library from scratch.

## Prerequisites

- **Library System** must be installed first (see `Feature/Library-System/`)
- Working `library/` directory with section folders

## How to Install

```
"install item security-headers"
```

AI will:
1. Find item in `library-items/`
2. Show you what it contains
3. Copy to `library/[section]/` folder
4. Commit the change (if Auto-Commit installed)

Or browse items manually and copy any `.md` file directly into `library/[section]/`.

## Available Items

| Section | Item | Description |
|---------|------|-------------|
| `security` | `security-headers` | HTTP security headers with CSP — framework-agnostic (Laravel, Express, Spring Boot, Nginx/Apache) |

## Item Format

Each item follows its section's format template. Items ready to use as-is — customize as needed.

## Contributing Items

Create `.md` file following appropriate format template:

1. Pick right section folder (or create new one)
2. Follow format from `Feature/Library-System/formats/[section]-format.md`
3. Write generic, reusable content — no project-specific references
4. Include implementation examples for multiple frameworks where applicable
5. Submit pull request

### Guidelines
- **Generic over specific** — items should work across projects and frameworks
- **Production-tested** — only share patterns used in real projects
- **Format-compliant** — follow the section's format template
- **Self-contained** — each item usable without external dependencies

---

*Solve it once, share it forever*
