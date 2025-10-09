# Copilot Instructions for TMS Documentation

## Project Overview

This is a **VitePress-based documentation site** for the Tourist Management System (TMS), featuring extensive diagram-as-code documentation using PlantUML and D2. The project documents software requirements, use cases, sequence diagrams, activity diagrams, and database schemas.

## Architecture & Key Components

- **VitePress**: Static site generator with custom theme (Catppuccin)
- **vitepress-plugin-diagrams**: Renders PlantUML/D2 diagrams via Kroki server
- **Kroki Server**: External diagram rendering service (Docker: `yuzutech/kroki:8000`)
- **Structure**: `docs/` contains all markdown files organized by document type

## Development Workflow

### Running the Dev Server

```bash
just run              # Uses justfile
# OR
npm run docs:dev      # Direct command
```

### Building & Preview

```bash
npm run docs:build    # Build static site
npm run docs:preview  # Preview production build
```

### Diagram Rendering

- **CRITICAL**: Start Kroki server first: `docker compose up -d`
- Set `KROKI_SERVER_URL` environment variable if not using default `http://localhost:8000`
- Without Kroki, diagrams won't render during development

## File Organization & Naming Conventions

### Documentation Structure

```
docs/docs/
├── activity/        # Activity diagrams (PlantUML)
├── sequence/        # Sequence diagrams (PlantUML)
├── use-case/        # Use case diagrams (PlantUML)
├── database/        # Database schemas (D2)
├── srs/            # Software Requirements Specification
└── function-list/   # Feature matrix
```

### Naming Rules (CRITICAL)

1. **Markdown Headers**:

   - Activity files: Start with `# Activity {Name}`
   - Sequence files: Start with `# Sequence {Name}`
   - Use Case files: Start with `# Use Case {Name}`

2. **Diagram IDs** (REQUIRED to prevent storage leaks):

   ```markdown
   <!-- diagram id="{type}-{subfolder}-{filename}" -->
   ```

   Examples:

   - `<!-- diagram id="sequence-manage-user-search-user" -->`
   - `<!-- diagram id="activity-view-product-add-to-cart" -->`
   - `<!-- diagram id="use-case-customer" -->`

3. **Generic Use Cases**: When filename matches parent folder (e.g., `view-product/view-product.md`), it's a "container" diagram that references sub-diagrams using `ref` (sequence) or conditional branches (activity)

## Diagram Patterns

### Sequence Diagrams

- Use PlantUML syntax with `@startuml`/`@enduml`
- **Participants**: Customer (C), System boundaries (View), Controllers, Database entities
- **Generic pattern**: Use `opt` blocks with `ref over` to link sub-sequences
- **Search pattern**: Show validation → query → results flow
- **CRUD pattern**: Show data retrieval/modification flow
- **Don't deactivate** execution bars inside `opt`/`alt`/`break` blocks

### Activity Diagrams

- Three swimlanes: Actor (e.g., `|C|Customer`), `|S|System`, `|D|Database`
- **Generic pattern**: Use `if/elseif/else` blocks to branch to sub-activities
- **Search pattern**: Show input validation loops
- **CRUD pattern**: Show step-by-step user-system-database interactions
- Number steps like `(1)`, `(2)`, `(2.1)` for sub-steps

### Database Diagrams (D2)

- Use D2 syntax with `**.shape: sql_table`
- Include constraints: `{constraint: PK}`, `{constraint: FK}`, `{constraint: UNQ}`
- Use `elk` layout engine: `d2-config: {layout-engine: elk}`

## Key Files to Reference

- **Diagram examples**: `docs/docs/sequence/view-product/view-product.md`
- **Database schema**: `docs/docs/database/index.md`
- **SRS document**: `docs/docs/srs/index.md` (1074 lines, comprehensive requirements)
- **VitePress config**: `docs/.vitepress/config.mts` (sidebar navigation)
- **AI workspace rules**: `.rules/*.md` (detailed diagram conventions)

## Project-Specific Patterns

1. **Diagram ID Management**: Always include diagram IDs to prevent SVG file proliferation in `docs/public/diagrams/`
2. **Three-tier Architecture**: UI (Views) → Controllers → Database entities
3. **Authentication Flow**: Uses PKCE (code verifier/challenge) → authorization code → JWT
4. **Multi-role System**: Customer, Staff, Admin with distinct workflows
5. **Catppuccin Theme**: Uses both Latte (light) and Mocha (dark) variants

## Common Pitfalls

- ❌ Forgetting diagram IDs → generates new SVG files each build
- ❌ Not starting Kroki server → diagrams fail to render
- ❌ Incorrect header prefixes → breaks navigation/search
- ❌ Wrong diagram ID format → doesn't match file structure
- ❌ Deactivating participants inside control flow blocks → breaks diagram rendering

## External Dependencies

- **Node.js**: ≥24.8.0 (managed via mise/nvm)
- **Kroki**: Docker container for diagram rendering
- **PlantUML/D2**: Rendered server-side via Kroki
