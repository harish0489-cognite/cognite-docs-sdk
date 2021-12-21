---
sidebar_position: 2
---

# Authentication

How to authenticate using **OIDC** :
<!-- 
- a **sidebar**
- **previous/next navigation**
- **versioning**

## Create your first Doc -->
<!-- 
Create a markdown file at `docs/hello.md`: -->

<!-- ```md title="docs/hello.md"
# Hello

This is my **first Docusaurus document**!
``` -->
<!-- 
A new document is now available at `http://localhost:3000/docs/hello`.

## Configure the Sidebar

Docusaurus automatically **creates a sidebar** from the `docs` folder.

Add metadatas to customize the sidebar label and position: -->
<!-- 

```md title="docs/hello.md" {1-4}
---
sidebar_label: 'Hi!'
sidebar_position: 3
---

# Hello

This is my **first Docusaurus document**!
```

It is also possible to create your sidebar explicitly in `sidebars.js`:

```diff title="sidebars.js"
module.exports = {
  tutorialSidebar: [
    {
      type: 'category',
      label: 'Tutorial',
-     items: [...],
+     items: ['hello'],
    },
  ],
};
``` -->

``` md title="OIDC Auth" 
import { Configuration, PublicClientApplication } from "@azure/msal-browser";
import { CogniteClient } from "@cognite/sdk";

const cluster = process.env.REACT_APP_CLUSTER || 'api'
const baseUrl = `https://${cluster}.cognitedata.com`;

const scopes = [
  `${baseUrl}/DATA.VIEW`,
  `${baseUrl}/IDENTITY`
];

// MSAL configuration
const configuration: Configuration = {
  auth: {
    clientId: "$AZURE_APP_ID",
    authority: "https://login.microsoftonline.com/$AZURE_TENANT_ID",
  },
};

const pca = new PublicClientApplication(configuration);
const getToken = async () => {
  const accountId = "some-id";
  const account = pca.getAccountByLocalId(accountId)!;
  const token = await pca.acquireTokenSilent({
    account,
    scopes,
  }).catch(e => {
    return pca.acquireTokenPopup({
    account,
    scopes,
    });
  });
  return token.accessToken;
};


const client = new CogniteClient({
  project: "my-project",
  appId: "demo-sample",
  getToken
});
```
