# Istvan Hoka - Personal Website

A modern personal website and CV built with Jekyll and Tailwind CSS. Features a dark theme with glassmorphism effects, gradient styling, and interactive elements.

## Development Setup

### Prerequisites

- [mise](https://mise.jdx.dev/) - for tool management
- Ruby and Bundler - for Jekyll

### Getting Started

1. Install dependencies:

   ```bash
   mise install
   bundle install
   ```

2. Start the development server:

   ```bash
   mise run dev
   ```

   This will:
   - Start Jekyll with live reload enabled
   - Open your browser automatically
   - Watch for file changes and refresh the page
   - Use incremental builds for faster updates

### Available Commands

- `mise run dev` - Start development server with live reload
- `mise run lint` - Check markdown files for linting issues
- `mise run lint-fix` - Automatically fix markdown formatting issues

## Structure

- `index.md` - Homepage with name and social links
- `cv.md` - Full CV content
- `_layouts/index.html` - Layout for homepage (vertically centered with glassmorphism)
- `_layouts/cv.html` - Layout for CV page (standard document layout)
- `_tailwind.css` - Custom Tailwind CSS styles and components
- `assets/css/styling.tailwindcss` - Jekyll frontmatter file for CSS processing
- `mise.toml` - Tool and task configuration

## Styling

The site features a modern dark theme with:

- **Dark background**: Deep navy (`#030712`)
- **Gradient text effects**: Custom CSS gradients for name and bullet points
- **Glassmorphism elements**: Frosted glass effect for social links container
- **Interactive animations**: Hover effects and 3D rotation on name
- **Monospace typography**: Courier New for name display
- **Tailwind CSS**: Integrated via jekyll-tailwindcss plugin

### CSS Architecture

- Custom styles in `_tailwind.css` are scoped to specific page IDs
- Home page styles use `#home-page` selector for isolation
- Glassmorphism effects use `backdrop-filter: blur()` and gradient backgrounds
- Text gradients use `background-clip: text` for modern styling

## Features

- **Homepage**: Clean, centered layout with gradient name styling and social links
- **CV Page**: Professional document layout with comprehensive work history
- **Responsive Design**: Works on desktop and mobile devices
- **Google Analytics**: GA4 tracking integrated
- **Favicon**: Custom IH initials favicon
- **Development Tools**: Live reload with mise and Jekyll

### Author

- Istvan Hoka ([ihoka.me](http://www.ihoka.me))

### License

[MIT License](https://github.com/elipapa/markdown-cv/blob/master/LICENSE)
