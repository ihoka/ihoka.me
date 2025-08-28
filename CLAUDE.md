# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static site serving as a personal CV/resume website. The site uses Tailwind CSS for styling and is built with a minimalist, dark theme design.

## Development Commands

- `mise run dev` - Start Jekyll development server with live reload, incremental builds, and auto-open browser
- **Note**: The dev server runs continuously in the background as a VSCode task - no need to start it manually

## Build Process

The site uses Jekyll with the `jekyll-tailwindcss` plugin for CSS processing:

1. **Tailwind CSS source**: `_tailwindcss.css` (imports tailwindcss)
2. **Jekyll processes**: `assets/css/styling.tailwindcss` (Jekyll frontmatter file)
3. **Output**: `_site/assets/css/styling.css` (final CSS file)

The CSS file referenced in layouts is `/assets/css/styling.css` - ensure this path matches the Jekyll processing pipeline.

## Architecture

### File Structure

- `_layouts/` - Jekyll templates (index.html for homepage, cv.html for CV page)
- `_site/` - Generated site output (don't edit directly)
- `assets/css/` - Styling source files
- `index.md` - Homepage content
- `cv.md` - CV page content

### Styling System

- **Framework**: Tailwind CSS integrated via jekyll-tailwindcss plugin
- **Theme**: Dark theme (bg-gray-900, text-gray-100)
- **Typography**: Monospace font for name display
- **Layout**: Centered homepage, standard document layout for CV

## Development Environment

### Tool Management

- **mise** manages tool versions (Ruby 3.3.1, Node.js, etc.)
- **Bundler** manages Ruby gem dependencies
- Run `mise install` to install required tools

### Configuration Files

- `mise.toml` - Tool versions and task definitions
- `_config.yml` - Jekyll site configuration
- `.markdownlint.json` - Markdown linting rules (line length disabled, HTML tags allowed)

## Code Style Guidelines

- **NO HTML IN MARKDOWN**: NEVER add ANY HTML tags to markdown files (.md files). Use pure markdown only
- **CSS-ONLY STYLING**: All styling must be done through CSS only (_tailwind.css file). Use CSS selectors and pseudo-elements to style the generated HTML markup
- **Styling**: All styling should go through Tailwind CSS system  
- **CSS Processing**: Use the Jekyll + Tailwind CSS pipeline, don't write raw CSS
- **Layouts**: Keep layouts minimal and focused on structure
- **Content**: Separate content (markdown) from presentation (layouts)

## Common Tasks

### Adding New Styles

1. Use Tailwind CSS utility classes in layouts
2. For custom styles, extend the Tailwind configuration
3. CSS is processed through `assets/css/styling.tailwindcss` → `_site/assets/css/styling.css`

### Content Updates

- Homepage: Edit `index.md`
- CV: Edit `cv.md`
- Layouts: Edit files in `_layouts/`

### Troubleshooting Styles

- Check that `_site/assets/css/styling.css` is being generated
- Verify the CSS file path in layouts matches the Jekyll output
- Ensure `assets/css/styling.tailwindcss` has proper Jekyll frontmatter

## Testing

Currently minimal testing setup. Planned:

- Unit tests for link validation
- CI/CD pipeline setup (GitLab)
