# Blog Style Improvements Spec

## Problem Statement

The blog has visual design issues that affect readability and professional appearance:

1. **No syntax highlighting** - All code blocks display in monochrome red regardless of language
2. **Diagrams styled as code** - ASCII diagrams (`txt` blocks) receive code syntax styling when they should be plain text
3. **Bullet alignment issues** - List items lack proper indentation and multi-line alignment
4. **Missing fenced code block styling** - No CSS for `pre` elements, only inline `code`

## Current State

### Rouge Already Configured

`_config.yml` already has Rouge syntax highlighter enabled:

```yaml
markdown: kramdown
kramdown:
  input: GFM
  syntax_highlighter: rouge
```

**The problem**: Rouge generates HTML with CSS classes (`.highlight .k` for keywords, etc.) but there's no CSS to style them. Everything renders as default text color.

### Code Block Styling (`_tailwind.css:239-254`)

```css
#blog-page code {
    background-color: var(--code-bg);
    color: var(--code-text);  /* #ff0000 in dark mode */
    padding: 0.125rem 0.25rem;
    border-radius: 0.25rem;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
}
```

**Problem**: Only styles inline `code`, not `pre code` blocks. Uses single red color.

### Bullet Styling (`_tailwind.css:256-275`)

```css
#blog-page ul {
    list-style: none;
    padding-left: 0;  /* No indent */
    margin: 1rem 0;
}

#blog-page ul li {
    display: flex;
    align-items: baseline;
    padding-left: 0;  /* No indent */
}
```

**Problem**: No left padding causes bullets to align flush with paragraph text.

## Proposed Changes

### 1. Add Rouge Syntax Highlighting Theme

Rouge includes a CLI (`rougify`) that generates theme CSS. Available dark themes:

- `monokai.sublime` - Classic Monokai (recommended for dark theme)
- `github.dark` - GitHub's dark mode
- `gruvbox.dark` - Gruvbox dark variant
- `base16.monokai.dark` - Base16 Monokai

Generate theme CSS:

```bash
bundle exec rougify style monokai.sublime --scope '#blog-page .highlight' >> _tailwind.css
```

This adds ~150 lines of CSS that styles Rouge's generated classes.

### 2. Add Fenced Code Block Styling

Add distinct styling for multi-line code blocks (`pre code`):

```css
#blog-page .highlighter-rouge {
    margin: 1rem 0;
}

#blog-page .highlight {
    background-color: var(--code-bg);
    border-radius: 0.5rem;
    padding: 1rem;
    overflow-x: auto;
}

#blog-page .highlight pre {
    margin: 0;
    padding: 0;
    background: transparent;
}

#blog-page .highlight code {
    background-color: transparent;
    padding: 0;
    color: var(--text-primary);
    font-weight: normal;
    font-size: 0.875rem;
    line-height: 1.5;
}

/* Remove backticks from block code */
#blog-page .highlight code::before,
#blog-page .highlight code::after {
    content: none;
}
```

### 3. Style Diagrams Differently

Diagrams (language: `txt` or `text`) should NOT have syntax highlighting. Style them as plain monospace text:

```css
/* Plain text/diagram blocks - muted color, no syntax highlighting */
#blog-page .language-txt .highlight,
#blog-page .language-text .highlight,
#blog-page .highlight.language-txt,
#blog-page .highlight.language-text {
    color: var(--text-secondary);
}

#blog-page .language-txt .highlight *,
#blog-page .language-text .highlight * {
    color: inherit !important;
}
```

### 4. Fix Bullet Alignment

Add proper indentation for lists:

```css
#blog-page ul {
    list-style: none;
    padding-left: 1.5rem;
    margin: 1rem 0;
}

#blog-page ul li {
    margin: 0.5rem 0;
    padding-left: 0.5rem;
    position: relative;
    display: block;  /* Changed from flex */
}

#blog-page ul li::before {
    content: "*";
    position: absolute;
    left: -1rem;
    color: var(--accent);
    font-weight: bold;
}

/* Nested lists */
#blog-page ul ul {
    padding-left: 1.5rem;
    margin: 0.5rem 0;
}
```

### 5. Add Ordered List Styling

Currently missing - ordered lists need styling:

```css
#blog-page ol {
    list-style: none;
    padding-left: 2rem;
    margin: 1rem 0;
    counter-reset: item;
}

#blog-page ol li {
    margin: 0.5rem 0;
    padding-left: 0.5rem;
    position: relative;
    counter-increment: item;
}

#blog-page ol li::before {
    content: counter(item) ".";
    position: absolute;
    left: -1.5rem;
    color: var(--accent);
    font-weight: bold;
    font-family: 'Courier New', Courier, monospace;
}
```

### 6. Keep Inline Code Styling Distinct

Ensure inline `code` keeps its current styling (red with backticks):

```css
/* Inline code (not in pre blocks) */
#blog-page p code,
#blog-page li code,
#blog-page td code {
    background-color: var(--code-bg);
    color: var(--code-text);
    padding: 0.125rem 0.25rem;
    border-radius: 0.25rem;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
}

#blog-page p code::before,
#blog-page li code::before,
#blog-page td code::before {
    content: "`";
}

#blog-page p code::after,
#blog-page li code::after,
#blog-page td code::after {
    content: "`";
}
```

## Implementation Steps

1. Generate Rouge theme CSS using `rougify`
2. Add fenced code block base styling to `_tailwind.css`
3. Add diagram-specific overrides for `txt`/`text` language
4. Fix bullet list indentation
5. Add ordered list styling
6. Refactor inline code selectors to be more specific
7. Test on DIP blog post

## Files to Modify

- `_tailwind.css` - All CSS changes

## Out of Scope

- Changing the overall color scheme/theme
- Modifying homepage or CV page styles
- Adding new gems or JavaScript dependencies
- Mobile-specific responsive changes

## Acceptance Criteria

- [ ] Java code blocks show multi-color syntax highlighting (keywords, strings, comments differentiated)
- [ ] ASCII diagrams (`txt` blocks) display as plain monospace text without syntax colors
- [ ] Bullet points properly indented from paragraph text
- [ ] Multi-line bullet items wrap with proper alignment
- [ ] Numbered lists styled consistently with bullets
- [ ] Code blocks have visible background container with rounded corners
- [ ] Inline `code` remains styled with red color and backticks
- [ ] No horizontal scrollbar on code blocks unless content overflows
