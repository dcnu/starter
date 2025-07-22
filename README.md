# Starter Template

A modern software development project template with opinionated defaults for web applications and CLI tools.

## Features

- **Next.js 15.4+** with App Router and TypeScript
- **TailwindCSS** with shadcn/ui components
- **Python CLI tools** with argparse and pytest
- **Pre-configured linting** with ESLint and Prettier
- **Git workflow** with conventional commits
- **AI crawler protection** via robots.txt

## Quick Start

1. **Clone and setup**
   ```bash
   git clone <repo-url>
   cd starter
   npm install
   ```

2. **Initialize project**
   ```bash
   git init
   git remote add origin <your-repo>
   # Uncomment IDE/Development sections in .gitignore for new projects
   ```

3. **Development**
   ```bash
   npm run dev        # Start Next.js dev server
   npm run lint       # Check code style
   npm run build      # Build for production
   npm test           # Run tests
   ```

## Directory Structure

```
root/
├── .gitignore
├── README.md
├── CLAUDE.md          # AI assistant instructions
├── TODO/
│   ├── requirements.md
│   ├── architecture.md
│   └── tasks.md
├── src/
│   ├── app/           # Next.js pages (App Router)
│   ├── components/    # React components
│   ├── lib/          # Utilities
│   └── types/        # TypeScript types
├── tests/
├── output/           # Generated files
└── robots.txt        # AI crawler protection
```

## Tech Stack

- **Frontend**: Next.js, TypeScript, TailwindCSS, shadcn/ui
- **Backend**: Node.js API routes, Supabase/PostgreSQL
- **Testing**: Jest, React Testing Library, pytest
- **Deployment**: Vercel
- **Tools**: ESLint, Prettier, GitHub CLI

## Development Standards

### Code Quality
- All TypeScript files must be typed
- Use tabs for indentation
- Pre-build validation (lint + typecheck + test)
- Single responsibility principle

### Git Workflow
- Use `main` branch
- Commit format: `Type: description` (under 50 chars)
- Valid types: Init, Add, Fix, Refactor, Test, Docs, Remove, Update

### Python Standards
- CLI-first with `argparse`
- Standard library only unless explicitly allowed
- UTF-8 encoding, proper error handling
- Type hints and docstrings

## Environment Setup

**Requirements:**
- macOS with Homebrew
- Node.js 18+
- Python 3+
- Git and GitHub CLI

**Install dependencies:**
```bash
brew install node python git gh
npm install
pip install -r requirements.txt
```

## AI Protection

This template includes comprehensive AI crawler blocking via `robots.txt`, preventing:
- Training data collection from major AI companies
- SEO and commercial crawlers
- Search engine indexing (configurable)

## License

GPL-3.0