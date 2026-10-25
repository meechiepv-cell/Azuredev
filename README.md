# Azuredev

A minimal, deploy-ready Node.js starter from **Cyber Digits Inc** — a landing page for the "365" suite that deploys to Azure App Service on every push to `main`. Zero dependencies, Node 20.

## Run locally

```bash
npm start
```

Then open http://localhost:3000. Health check: http://localhost:3000/api/health

## Deploy to Azure (one-time setup)

1. **Azure portal → create a Web App** (Linux, Node 20 runtime). Note its name.
2. **Download the publish profile**: Web App → Overview → Get publish profile.
3. **GitHub repo → Settings → Secrets and variables → Actions → New repository secret**:
   - Name: `AZURE_WEBAPP_PUBLISH_PROFILE`
   - Value: paste the entire publish profile file contents.
4. **Set the app name**: in `.github/workflows/azure-webapps-node.yml`, change `AZURE_WEBAPP_NAME` from `your-app-name` to your Web App's name.
5. **Push to `main`.** The workflow builds and deploys automatically; the deployed URL appears in the Actions run output.

Notes:

- The workflow file in this scaffold is the same standard Azure template already in the repo — only the app name needs setting.
- Keep `FUNDING.yml` as-is; this scaffold does not replace it.
- To grow the app: add pages under `public/` and API routes in `server.js`. If you add dependencies later, they install automatically in the workflow's `npm install` step.
