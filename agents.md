# Agent Guide for Arancini

This document provides guidance for AI agents working on the arancini Hugo theme.

## Repository Overview

**arancini** is a minimalist, responsive Hugo theme with full base16 color scheme support and enhanced syntax highlighting. It is forked from [risotto](https://github.com/joeroe/risotto) by Joe Roe.

### Key Features
- Plain, semantic HTML with no JavaScript
- CSS Grid-based responsive design (no arbitrary breakpoints)
- 24 built-in base16 color palettes (16 dark, 8 light)
- Enhanced syntax highlighting that adapts to base16 schemes
- Full base16 variable support for theming consistency

## Architecture

### Directory Structure

```
arancini/
├── archetypes/          # Content templates
├── exampleSite/         # Demo site with sample configuration
├── layouts/             # Hugo template files
│   ├── _default/        # Default templates (list, single, baseof)
│   ├── partials/        # Reusable template components
│   └── post/            # Post-specific layouts
├── static/
│   └── css/             # All stylesheets
│       ├── palettes/    # Base16 color scheme definitions
│       ├── arancini.css # Main stylesheet import
│       ├── colours.css  # Base16 color variables
│       ├── syntax.css   # Chroma syntax highlighting
│       ├── typography.css
│       ├── layout.css
│       ├── header.css
│       ├── footer.css
│       ├── logo.css
│       ├── about.css
│       └── custom.css   # User customization entry point
└── images/              # Theme screenshots
```

### Core Concepts

#### 1. Base16 Color System
The theme uses the [base16 framework](https://github.com/chriskempson/base16) for color management:

- **16 color variables** (base00-base0F) defined per palette
- CSS variables provide consistent theming across all elements
- Variables defined in `static/css/palettes/*.css`
- Referenced in `colours.css` as semantic names:
  - `--bg` (base00), `--inner-bg` (base01), `--off-bg` (base02)
  - `--muted` (base03), `--off-fg` (base04), `--fg` (base05)
  - Accent colors: base08-base0F (red, orange, yellow, green, cyan, blue, magenta, brown)

#### 2. Syntax Highlighting
Enhanced Chroma highlighting in `static/css/syntax.css`:
- Keywords → Purple (base0E)
- Names/Identifiers → Red (base08)
- Built-ins → Yellow (base0A)
- Functions → Blue (base0D)
- Strings → Green (base0B)
- Numbers → Orange (base09)
- Operators → Cyan (base0C)
- Comments → Muted (off-fg)

#### 3. Layout System
- Uses CSS Grid for responsive behavior
- No JavaScript required
- Main layout defined in `layouts/_default/baseof.html`
- Sidebar content controlled via `aside` template blocks

## Development Guidelines

### When Adding Features

1. **Maintain Minimalism**: Avoid adding JavaScript unless absolutely necessary
2. **Base16 Integration**: Use existing base16 variables for all colors
3. **Responsive by Default**: Leverage CSS Grid; avoid fixed breakpoints
4. **Semantic HTML**: Use proper HTML5 elements over divs with classes

### When Adding Color Schemes

1. Create a new file in `static/css/palettes/`
2. Define all 16 base16 variables (base00-base0F)
3. For light themes, reverse 00-07 (light to dark)
4. Test with syntax highlighting examples
5. Add scheme name to README.md palette list

### When Modifying Layouts

- **Core templates** are in `layouts/_default/`
- **Partials** for reusable components in `layouts/partials/`
- **Content-specific** layouts can override defaults
- Use Hugo's template lookup order: content type → layout → default

### When Updating Styles

- **Never modify existing palette files** (user customizations depend on them)
- Add new styles to appropriate modular CSS files:
  - `typography.css` → Font, text styling
  - `layout.css` → Grid, spacing, structure
  - `header.css` / `footer.css` → Navigation elements
  - `about.css` → Sidebar styling
- Use base16 variables (`var(--base0X)`) for all colors
- Test changes across multiple palettes (dark and light)

### Configuration Parameters

Key `config.toml` parameters to be aware of:

```toml
[params.theme]
palette = "nord"  # Default: nord

[params.about]
title = "Site Title"
description = "Description"
logo = "🧆"  # Emoji/Unicode character
logo_image = "path/to/image"  # Alternative image logo

[[params.socialLinks]]
icon = "fa-brands fa-github"  # FontAwesome 6 or Academicons
title = "GitHub"
url = "https://github.com/..."
```

## Testing Checklist

When making changes, verify:

- [ ] Works with at least 3 different palettes (1 light, 2 dark)
- [ ] Responsive behavior on mobile/tablet/desktop
- [ ] No JavaScript errors (there should be no JS!)
- [ ] Syntax highlighting displays correctly
- [ ] Valid HTML (no nested errors)
- [ ] Example site builds without errors: `hugo -s exampleSite`
- [ ] No CSS specificity conflicts

## Common Tasks

### Adding a New Palette

```bash
# 1. Create palette file
cat > static/css/palettes/my-palette.css << 'EOF'
:root {
  --base00: #...;
  --base01: #...;
  /* ... define all 16 colors ... */
}
EOF

# 2. Test it
cd exampleSite
hugo server --theme arancini --config config.toml
# Visit site and verify colors
```

### Debugging Layout Issues

1. Check `layouts/_default/baseof.html` for overall structure
2. Verify CSS Grid in `static/css/layout.css`
3. Use browser DevTools to inspect CSS variables
4. Test with `hugo server --disableFastRender`

### Adding Icon Support

The theme uses:
- **FontAwesome 6** (loaded from CDN in `layouts/partials/head.html`)
- **Academicons** (also from CDN)

To add icons:
```toml
[[params.socialLinks]]
icon = "fa-brands fa-mastodon"  # FontAwesome brand
icon = "ai ai-orcid"            # Academicons
```

## Important Files Reference

| File | Purpose |
|------|---------|
| `layouts/_default/baseof.html` | Base template structure |
| `layouts/partials/head.html` | HTML head, CSS includes |
| `layouts/partials/header.html` | Site navigation |
| `layouts/partials/about.html` | Sidebar content |
| `static/css/arancini.css` | Main CSS import file |
| `static/css/colours.css` | Base16 variable mappings |
| `static/css/syntax.css` | Syntax highlighting rules |
| `exampleSite/config.toml` | Reference configuration |

## Constraints & Conventions

### Do NOT:
- Add JavaScript (theme philosophy: plain HTML/CSS only)
- Use CSS preprocessors (keep it plain CSS)
- Modify base16 variable names (breaking change for users)
- Add npm/package manager dependencies
- Include large external assets (keep it minimal)

### DO:
- Use CSS Grid and Flexbox for layouts
- Keep CSS modular and semantic
- Maintain backward compatibility with risotto where possible
- Document breaking changes clearly in NEWS.md
- Test across multiple browsers
- Follow Hugo best practices for templates

## Version History Context

The theme evolved from risotto with these major changes:

- **v1.0.0**: Fork with enhanced syntax highlighting
- Inherited from risotto 0.4.0: base16 framework, TOC support, favicon support
- Original risotto used gruvbox; arancini defaults to nord

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Base16 Specification](https://github.com/chriskempson/base16)
- [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)
- [Chroma Syntax Highlighting](https://github.com/alecthomas/chroma)
- [FontAwesome 6 Icons](https://fontawesome.com/icons)
- [Academicons](https://jpswalsh.github.io/academicons/)

## Contact & Contribution

- **Maintainer**: Chad Metcalf
- **Repository**: https://github.com/metcalfc/arancini
- **Original Theme**: https://github.com/joeroe/risotto (Joe Roe)

When contributing, follow the minimalist philosophy: if a feature requires JavaScript or adds significant complexity, consider if it truly belongs in a minimal theme.
