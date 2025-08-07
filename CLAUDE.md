# Claude Code

This file provides guidance to Claude Code (claude.ai/code) when working with code in any repository.

Added memories should be appended to this document, in the end section titled `Memory`.

## About Me
- Solo developer

## About You
- Succinct, unemotional
- No pleasantries, apologies, or compliments
- No exclamation points or emojis

### Coding Style
- **Iterative development**: build incrementally, one service at a time
- **No premature optimization**: optimize only after measuring performance
- **Single responsibility**: each service should have one well-defined purpose
- **Always test**: write tests before considering implementation complete
- **Design before code**: think through architecture before implementing
- Unless specifically asked, do NOT summarize changes made or benefits of changes after they have been made

* * * * * * * * * * * * * * * * * * * *

# Project Setup

## Tech Stack
Unless specified otherwise, use:
- **Frontend**: Next.js 15.4+ with App Router, TypeScript, TailwindCSS
  - **Sometimes:** Vue, Inertia.js
- **Backend**: Node.js 18+, API routes in Next.js
- **Database**: Supabase, PostgreSQL
- **Deployment**: Vercel
- **UI**: extend Tailwind default theme, shadcn/ui components, Lucide React icons

## Directory Structure
```
root/
├── .gitignore
├── README.md
├── TODO/
│   ├── requirements.md     # Product overview (never edit)
│   ├── architecture.md     # Repo overview
│   └── tasks.md            # Outstanding items
├── src/
│   ├── app/                # Next.js pages (App Router)
│   ├── components/         # React components
│   ├── lib/                # Utilities
│   └── types/              # TypeScript types
├── tests/
└── output/                 # Generated files
```

## Setup Process
1. Clarify if tool is CLI-only or requires web app
2. Initialize git repo with `main` branch
3. Install dependencies and verify build tools
4. Create directory structure and core files
5. Configure environment variables

## Environment Requirements
- macOS with `brew` installed
- Git and GitHub CLI (`gh`)
- Node.js 18+ (`node`, `npm`)
- Python 3+ (`python3`) for CLI tools

* * * * * * * * * * * * * * * * * * * *

# Development Standards

## Package Management
- `brew` for system packages
- `npm` for JavaScript packages (no `yarn` unless locked)
- `pip` with virtual environments for Python
- Never install globally unless required

## Pre-Build Validation
Run before every `npm run build`:
```bash
npm run lint      # Cok ode style and bugs
tsc --noEmit      # Type checking
npm test          # Unit tests
```

Build must fail if any of these fail. Add to `package.json`:
```json
"scripts": {
  "prebuild": "npm run lint && tsc --noEmit && npm test"
}
```

## Code Formatting
- Use `eslint` and `prettier` for JavaScript/TypeScript
- Use `pytest` for Python testing
- **Use tabs, NOT spaces, for indentation**
- No leading spaces for terminal commands
- Terminal commands in fenced code blocks may be indented for formatting

## Git Management
- Use `main` branch
- Commit frequently after meaningful changes
- Messages: `Type: description` (max 1 line; under 50 chars)
- Valid types: `Init`, `Add`, `Fix`, `Refactor`, `Test`, `Docs`, `Remove`, `Update`
- Never commit `.env*`, secrets, or output files
- Never mention Claude, Anthropic, or Cursor

### .gitignore
```
# Project specific
.cursor*
.claude*
CLAUDE.md
TODO*

# Environment files
.env*
```

## Security
- Environment variables in `.env.local` for secrets
- No API keys on frontend
- HTTPS everywhere with CSP
- No sensitive data in client code

* * * * * * * * * * * * * * * * * * * *

# Language Guidelines

## Python
- **Structure**: CLI-first with `argparse`, `if __name__ == "__main__"` guard
- **Style**: PEP 8, type hints, docstrings for all functions
- **Testing**: `pytest` in `tests/` directory
- **I/O**: UTF-8 encoding, proper error handling with non-zero exits
- **Imports**: Standard library only unless explicitly allowed

## TypeScript/JavaScript
- **All files must be typed**
- **Prefer server components** over client components
- **Use JSDoc** for function documentation
- **Jest + React Testing Library** for testing

## Next.js Specifics
- App Router only
- Pre-render pages when possible
- ISR for frequently updated content
- Semantic HTML (`main`, `nav`, `section`)
- `use client` only when necessary

* * * * * * * * * * * * * * * * * * * *

# Styling

## Tailwind CSS
- Utility-first approach
- Extract to `globals.css` if reused across multiple components
- Extend default theme, don't override unless explicitly given an alternative theme
- Support dark mode with `darkMode: "class"`
- Hide scrollbars by default
- Use responsive breakpoints (`sm`, `md`, `lg`, `xl`, `2xl`)

## Component Standards
- shadcn/ui for all UI components
- Lucide React for icons
- `min-h-screen` on pages
- Prevent layout shifts
- Mobile-first responsive design
- 12-column grid for desktop, constrained width

## Performance
- Lighthouse score > 90
- GPU-accelerated animations with `transform`
- Optimize images with Next.js Image component
- Privacy-focused analytics (Plausible/Umami)

* * * * * * * * * * * * * * * * * * * *

# Testing & Quality

## Testing Strategy
- **Python**: `pytest`, mirror directory structure in `tests/`
- **JavaScript**: Jest + React Testing Library
- **Files**: `*.test.{js,ts,jsx,tsx}` or `*_test.py`
- **Coverage**: Unit tests for functions, component tests for React, integration tests for APIs
- **Data**: Mock external dependencies, clean up after tests

## Error Handling
- **Python**: Specific exceptions, `logging` module, graceful `KeyboardInterrupt`
- **JavaScript**: Try/catch for async, error boundaries for React
- **APIs**: Consistent error formats, appropriate HTTP codes
- **Logging**: Structured logs, correlation IDs, sanitized sensitive data

## Code Quality
- Split long files and functions
- Comments only for complex logic
- No inline TODOs or commented code
- Remove empty directories after deleting files

* * * * * * * * * * * * * * * * * * * *

# Naming Conventions

## Python
- **Files**: `snake_case.py`
- **Variables/Functions**: `snake_case`
- **Classes**: `PascalCase`
- **Constants**: `UPPER_SNAKE_CASE`
- **CLI Args**: `--kebab-case`

## JavaScript/TypeScript
- **Components**: `PascalCase` (files and component names)
- **Utilities**: `camelCase`
- **API routes**: `kebab-case`
- **Action names**: `kebab-case`

## JSON
- **Keys:** `camelCase`
- Use Prettier for formatting

## Output Files
Format: `Source-Title-date.ext`
- Use `-` as delimiter
- `PascalCase` for titles
- `PascalCase` for sources, including authors, firms, or entities
  - For people, use LastnameFirstname (e.g. SmithJohn)
- Accepted formats for dates
  - `YYMMDD` if full date is known
  - `YYYY-Qn` (e.g. 2025-Q3) for quarterly content
  - `YYYY-Month` (e.g. 2025-July) if only year and month known
  - `YYYY` if only year known 
- Never overwrite without `--force`

* * * * * * * * * * * * * * * * * * * *

# Documentation

## README Requirements
- Project description and purpose
- Installation instructions
- Usage examples with CLI arguments
- Environment setup requirements
- Testing instructions

## Code Documentation
- **Python**: Google/NumPy docstring format
- **JavaScript**: JSDoc format
- Include purpose, parameters, return values, examples
- Document complex logic only

## API Documentation
- Request/response examples
- Authentication requirements
- Error response formats
- OpenAPI/Swagger for REST APIs

* * * * * * * * * * * * * * * * * * * *

# Memory

Use this space for information added in the terminal with a # command.

Do not make any edits above this line.

- When told to address a conflict, fix the conflict
  - Do not remove code to avoid finding a permanent solution