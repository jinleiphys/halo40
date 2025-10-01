# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Slidev presentation project for the HALO-40 symposium (International Symposium Commemorating the 40th Anniversary of the Halo Nuclei). The project includes a custom Slidev theme called `nucl-th` designed for academic presentations in nuclear physics.

## Key Commands

### Development
- `npm run dev` - Start development server from root directory (recommended - uses ./nucl-th theme)
- `cd nucl-th && npm run dev` - Start development server from theme directory (uses example.md)
- `cd nucl-th && npx slidev slides.md --open` - Run specific slides file from theme directory

### Build and Export
- `npm run build` - Build presentation for production
- `npm run export` - Export slides to PDF
- `cd nucl-th && npm run screenshot` - Export slides as PNG images

### Dependency Management
- `npm install` - Install/update dependencies (updates package-lock.json)
- `npm ci` - Clean install from lock file (used in GitHub Actions as `nci` via @antfu/ni)

## Architecture

### Project Structure
- **`slides.md`** - Main presentation content (root level)
- **`pics/`** - Image assets for slides
- **`pages/`** - Additional slide pages
- **`snippets/`** - Code snippets for presentations
- **`nucl-th/`** - Custom Slidev theme directory

### Theme Structure (`./nucl-th/`)
The custom `nucl-th` theme provides academic presentation styling with these key components:

- **`package.json`** - Theme configuration with scripts and dependencies
- **`index.ts`** - Main theme entry point that imports styles and exports components
- **`styles/index.ts`** - Style imports (fonts, layout CSS)
- **`styles/layout.css`** - Main theme styling with academic color scheme and typography
- **`layouts/`** - Vue layout components:
  - `cover.vue` - Title slide with author affiliations and meeting info
  - `default.vue` - Standard slide layout with bottom bar
  - `intro.vue` - Introduction slide layout
- **`components/`** - Reusable Vue components:
  - `BarBottom.vue` - Bottom navigation bar with author, title, meeting info
  - `TextBox.vue` - Styled content boxes for highlights
- **`example.md`** - Theme example slides for development

### Author Format
The theme supports a custom author format for academic presentations:
```yaml
authors: 
  - "Author Name": ["Affiliation 1", "Affiliation 2"]
```

### Meeting Configuration
Two meeting fields are supported:
- `meeting` - Full meeting name (displayed on cover slide)
- `meetingShort` - Short name (displayed in bottom bar, e.g., "HALO-40")

### Color Scheme
- Primary: `#0FA3B1` (teal blue)
- Secondary: `#4EC5D4` (light blue)
- Accent: `#146b8c` (dark blue)
- Meeting text: `#B8860B` (dark golden rod)

### Fonts
- Sans: Inter (body text, UI elements)
- Serif: Crimson Pro (headings, formal text)
- Mono: JetBrains Mono (code blocks)

## Development Notes

### Theme Loading
- **Always run development server from the root directory** (`npm run dev`) to avoid component resolution issues
- The theme uses relative imports and expects proper file structure
- Logo file is located at `nucl-th/logo.png`
- **Critical**: Avoid having a `components/` directory at the root level as it conflicts with theme component resolution

### CSS Customizations
- Content positioning can be adjusted via `.slidev-layout` padding and h1 margins in `layout.css`
- Bottom bar styling is in `BarBottom.vue` component
- Cover slide styling is in the `.slidev-layout.cover` section of `layout.css`

### Slide Content
Main presentation content is in `slides.md` at the project root, configured to use the `./nucl-th` theme.

## Deployment

### GitHub Pages
- Automatic deployment via GitHub Actions on push to main branch
- Manual deployment via workflow_dispatch trigger
- Built presentation available at: `https://[username].github.io/halo40/`
- Uses `@antfu/ni` package manager (commands: `nci` for install, `nr build` for build)
- Base path is automatically set to repository name during GitHub Actions build

### Font Dependencies
The project requires font packages in the main package.json for successful builds:
- `@fontsource/inter`, `@fontsource/crimson-pro`, `@fontsource/jetbrains-mono`
- Both package.json and package-lock.json must be synchronized
- Run `npm install` after adding dependencies to update the lock file

## Troubleshooting

### Component Resolution Issues
If you encounter errors like "ENOENT: no such file or directory, open '/components/BarBottom.vue'":
- Ensure no `components/` directory exists at the root level
- Move any root-level components to `components_backup/` or remove them
- Always run development from root directory with `npm run dev`

### Theme Development
- Theme has its own package.json and dependencies in `nucl-th/`
- Theme scripts: `dev` (uses example.md), `build`, `export`, `screenshot`
- Theme fonts are declared in both theme and root package.json for deployment compatibility