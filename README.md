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

### Option 1: Azure CLI

1. Install the Azure CLI: https://learn.microsoft.com/cli/azure/install-azure-cli
2. Run `az login`
3. Choose your subscription: `az account set --subscription "<subscription-name-or-id>"`
4. Create a resource group and App Service:
   - `az group create --name portfolio-rg --location eastus`
   - `az appservice plan create --name portfolio-plan --resource-group portfolio-rg --sku B1 --is-linux`
   - `az webapp create --resource-group portfolio-rg --plan portfolio-plan --name <your-app-name> --runtime "NODE|18-lts"`
5. Deploy from the repository root:
   - `az webapp deploy --resource-group portfolio-rg --name <your-app-name> --src-path .`

You can also run the provided helper script:

```powershell
.\deploy-azure.ps1 -WebAppName "your-app-name"
```

### Option 2: GitHub Actions

A GitHub Actions workflow has been added at `.github/workflows/azure-webapp-deploy.yml`.

Set these repository secrets in GitHub:
- `AZURE_WEBAPP_NAME`
- `AZURE_PUBLISH_PROFILE`

Then push to `main` and GitHub will deploy the site automatically.
