# Vercel Web Analytics Setup Guide

This project has been configured to use Vercel Web Analytics.

## Installation

The `@vercel/analytics` package has been installed as a dependency in `package.json`.

```bash
npm install @vercel/analytics
```

## Configuration Options

Depending on your application structure, choose one of the following integration methods:

### Option 1: For HTML Files (Recommended for Express serving static HTML)

If your Express server serves HTML files from a `public` folder or similar, add this script tag to your main HTML file(s) (e.g., `index.html`):

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- Your existing head content -->
  </head>
  <body>
    <!-- Your existing body content -->
    
    <!-- Add Vercel Analytics script before closing body tag -->
    <script type="module">
      import { inject } from '@vercel/analytics';
      inject();
    </script>
  </body>
</html>
```

**Note:** This requires your HTML to be served with module support. If you encounter issues with ES modules, use Option 2 below.

### Option 2: Server-Side Integration

If you need to inject analytics from the server side, you can use the following approach in your Express server:

1. Create a middleware or use a templating engine
2. Inject the analytics script into your HTML responses

Example middleware for Express:

```javascript
// In your server/index.js or main server file
const express = require('express');
const app = express();

// Middleware to inject analytics
app.use((req, res, next) => {
  const originalSend = res.send;
  res.send = function(data) {
    if (typeof data === 'string' && data.includes('</body>')) {
      // Inject analytics script before closing body tag
      const analyticsScript = `
        <script type="module">
          import { inject } from '@vercel/analytics';
          inject();
        </script>
      `;
      data = data.replace('</body>', `${analyticsScript}</body>`);
    }
    originalSend.call(this, data);
  };
  next();
});

// Your routes and other middleware...
```

### Option 3: Using a Bundler (Webpack, Vite, etc.)

If you're using a bundler for your frontend assets, add this to your main entry file (e.g., `main.js`, `app.js`):

```javascript
import { inject } from '@vercel/analytics';

inject();
```

## Enabling Analytics in Vercel Dashboard

To start collecting analytics data:

1. Log in to your Vercel dashboard
2. Navigate to your project
3. Go to the "Analytics" tab
4. Click "Enable Web Analytics"

## Development vs Production

The analytics library automatically detects the environment:
- In development (localhost), events are logged to console
- In production (Vercel deployment), events are sent to Vercel Analytics

## Verification

After deploying your application:

1. Visit your deployed site
2. Navigate through a few pages
3. Return to the Vercel Analytics dashboard
4. You should see analytics data appearing within a few minutes

## Resources

- [Vercel Analytics Documentation](https://vercel.com/docs/analytics)
- [Quickstart Guide](https://vercel.com/docs/analytics/quickstart)
