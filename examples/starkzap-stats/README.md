# Starkzap Stats Dashboard

A static HTML dashboard for tracking npm download analytics for the `starkzap` package.

![Starkzap Stats Dashboard](./preview.png)

## Features

- **Live Data**: Fetches real-time download data from npm registry API
- **Four Views**:
  - **Daily**: Individual daily download counts
  - **Weekly**: Aggregated by ISO week
  - **Monthly**: Aggregated by calendar month
  - **Cumulative**: Running total over time
- **Summary Stats**: Total downloads, daily average, this week, this month
- **Responsive Design**: Works on desktop and mobile
- **No Build Required**: Single HTML file with embedded CSS/JS

## Quick Start

### Option 1: Open directly

```bash
# Just open the HTML file in your browser
open index.html
```

### Option 2: Serve locally

```bash
# Using Python
python -m http.server 8080

# Using Node.js (npx)
npx serve .

# Using PHP
php -S localhost:8080
```

Then visit `http://localhost:8080`

## Data Source

Download data comes from the npm registry API:

```
https://api.npmjs.org/downloads/range/{start}:{end}/starkzap
```

- **Start Date**: Fixed at `2025-01-01` (package creation)
- **End Date**: Automatically set to today's date

## Customization

### Change the package

Update the `PACKAGE_NAME` constant in the script:

```javascript
const PACKAGE_NAME = 'your-package-name';
```

### Change the start date

Update the `START_DATE` constant:

```javascript
const START_DATE = '2024-01-01';
```

### Styling

The dashboard uses CSS custom properties for theming:

```css
:root {
  --bg-primary: #0a0a0b;
  --bg-secondary: #131316;
  --accent-purple: #8b5cf6;
  --accent-blue: #3b82f6;
  /* ... */
}
```

## API Reference

### npm Downloads API

The npm registry provides download statistics via:

```
GET https://api.npmjs.org/downloads/range/{start}:{end}/{package}
```

**Response:**
```json
{
  "downloads": [
    { "day": "2025-01-01", "downloads": 42 },
    { "day": "2025-01-02", "downloads": 128 },
    // ...
  ]
}
```

## Browser Support

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

Requires `fetch` API and ES6+ support.

## Dependencies

- **Chart.js** (CDN): Used for rendering charts
- **No other dependencies**: Everything else is vanilla HTML/CSS/JS

## Related

- [starkzap on npm](https://www.npmjs.com/package/starkzap)
- [starkzap on GitHub](https://github.com/keep-starknet-strange/starkzap)
- [npm Downloads API docs](https://github.com/npm/registry/blob/master/docs/download-counts.md)

## License

MIT
