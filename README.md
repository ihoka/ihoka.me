# Istvan Hoka - CV

A curriculum vitae maintained in plain text and rendered to HTML using Jekyll and CSS. Features a dark theme with monospace styling and live reload for development.

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

- `index.md` - Homepage with name and CV link
- `cv.md` - Full CV content
- `_layouts/index.html` - Layout for homepage (vertically centered)
- `_layouts/cv.html` - Layout for CV page (standard document layout)
- `mise.toml` - Tool and task configuration

## Styling

The site uses a dark theme with:

- Dark background (`bg-gray-900`)
- Light text (`text-gray-100`)
- Monospace font for the name display
- Tailwind CSS via CDN for styling

### Author

- Istvan Hoka ([ihoka.me](http://www.ihoka.me))
- Eliseo Papa ([Twitter](http://twitter.com/elipapa)/[Github](http://github.com/elipapa)/[Website](https://elipapa.github.io)).

### License

[MIT License](https://github.com/elipapa/markdown-cv/blob/master/LICENSE)
