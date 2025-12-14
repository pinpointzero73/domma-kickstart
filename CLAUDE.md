# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Domma Kickstart is a starter template for building web applications with the Domma framework. Domma is a zero-dependency JavaScript framework that provides jQuery-compatible DOM manipulation, Lodash-compatible utilities, and a comprehensive UI component library.

## Architecture

### Core Namespaces

The Domma framework exposes the following global namespaces:

- **`Domma` or `$`**: DOM manipulation (jQuery-compatible API)
- **`_`**: Utility functions (Lodash-compatible, 120+ functions)
- **`M`**: Reactive models and pub/sub system
- **`D`**: Date manipulation (Moment-style API)
- **`S`**: LocalStorage wrapper with automatic JSON serialisation

### File Structure

```
/
├── index.html              # Main entry point with extensive documentation
├── includes/
│   └── index.js           # Application initialisation and examples
├── dist/                  # Domma framework files (pre-built)
│   ├── domma.min.js      # Core framework (~297KB)
│   ├── domma.css         # Base styles, typography, utilities
│   ├── grid.css          # Grid system (Bootstrap + CSS Grid)
│   ├── elements.css      # UI components (buttons, cards, modals, etc.)
│   └── themes/
│       └── domma-themes.css  # Theme system (light/dark + variants)
├── css/
│   └── custom.css        # Project-specific styles
└── assets/
    └── logo/             # SVG logos and icons
```

### CSS Load Order

CSS files must be loaded in this specific order:

1. `domma.css` - Base styles, typography, utilities
2. `grid.css` - Grid system
3. `elements.css` - UI components
4. `domma-themes.css` - Theme system
5. `custom.css` - Project-specific overrides

### JavaScript Load Order

1. `domma.min.js` - Core framework (must load first)
2. `index.js` - Application code

## Development Guidelines

### Working with Icons

Domma uses a data-attribute-based icon system:

```html
<span data-icon="document" data-icon-size="24"></span>
```

After adding icons to the DOM, call `Domma.icons.scan()` to render them as SVG elements.

### UI Components

Components are initialised via the `Domma.elements` namespace. Example:

```javascript
Domma.elements.navbar('#main-nav', {
    brand: { text: 'App', logo: 'path/to/logo.svg', url: '/' },
    items: [
        { text: 'Home', url: '/', active: true },
        { text: 'About', url: '/about' }
    ],
    variant: 'dark',
    collapsible: true,
    collapseAt: 768
});
```

### Theme System

Apply themes using body classes:
- `dm-theme-light` - Light theme (default)
- `dm-theme-dark` - Dark theme
- Additional variants available: ocean, forest, sunset, etc.

### CSS Variables

Domma provides extensive CSS custom properties:
- **Colours**: `--dm-primary`, `--dm-secondary`, `--dm-success`, `--dm-danger`, etc.
- **Spacing**: `--dm-space-1` through `--dm-space-16`
- **Typography**: `--dm-font-sans`, `--dm-font-mono`, `--dm-font-size-*`
- **Borders**: `--dm-radius-*`, `--dm-border`, `--dm-shadow-*`

### Grid System

Uses a 12-column grid with Bootstrap-compatible classes:
- `.container` - Max-width 1200px, centred
- `.row` - Flexbox row container
- `.col-{1-12}` - Column widths (e.g., `.col-4` = 33.33%)
- Responsive breakpoints: 576px (mobile), 768px (tablet), 992px (desktop), 1200px (wide)

## Common Patterns

### DOM Manipulation

```javascript
// jQuery-compatible API
$('.btn').on('click', function() {
    $(this).addClass('active').fadeOut(200).fadeIn(200);
});

// Finding elements
const elements = $('.selector');
console.log(elements.length);
```

### Utility Functions

```javascript
// Array operations
const doubled = _.map([1, 2, 3], n => n * 2);

// Object operations
const picked = _.pick(user, ['name', 'email']);

// Sorting
const sorted = _.sortBy(users, 'age');
```

### Storage API

```javascript
// Store complex objects
S.set('preferences', { theme: 'dark', lang: 'en' });

// Retrieve with automatic deserialisation
const prefs = S.get('preferences');

// Check existence
if (S.has('preferences')) { }

// Get all keys
const keys = S.keys();
```

### Date Manipulation

```javascript
// Create dates
const now = D();
const custom = D('2025-01-01');

// Format
now.format('MMMM D, YYYY [at] h:mm A');

// Arithmetic
D().add(7, 'days').subtract(2, 'hours');

// Relative time
D().fromNow();  // "2 hours ago"

// Comparison
nextWeek.isAfter(now);
```

## External Documentation

- **Main Documentation**: http://domma.dcbw-it.co.uk/showcase/index.html
- **Examples**: http://domma.dcbw-it.co.uk/examples/index.html
- **Download**: http://domma.dcbw-it.co.uk/showcase/download/index.html

## Notes

- This is a starter template, not the Domma framework source. The framework is pre-built in `dist/domma.min.js`.
- All framework files in `dist/` are production builds and should not be modified.
- Add customisations in `includes/index.js` and `css/custom.css`.
- The `index.html` file contains extensive inline documentation explaining each section.
- The framework requires no build tools or dependencies for development.