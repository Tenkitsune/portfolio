# Portfolio Site

A personal landing page with a simple Node.js server.

## Run locally

```bash
npm install
npm start
```

Then open `http://localhost:3000`.


## Notes

- `server.js` serves static assets and renders blog content from Markdown.
- `index.html` remains the homepage.


## Deploy to Azure App Service

This project is ready for Azure App Service deployment because `server.js` uses `process.env.PORT`.
