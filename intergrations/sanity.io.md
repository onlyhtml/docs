# Sanity.io

## Getting Started

We have built a starter project to make it super easy creating a new website with a sanity.io back-end. Getting a new project up and ready is as simple as

```bash
git clone git@github.com:onlyhtml/starter-sanity.git
cd starter-sanity
npm install
npm run init

# start the servers
npm run serve
```

## Connecting a CMS Manually

When ready, you can connect a headless CMS of your choice. Currently, only Sanity.io is supported. To connect sanity make sure `sanity-cli` is installed and run:

```bash
sanity init --output-path ./sanity-studio --template clean

cd sanity-studio
sanity install @onlyhtml/sanity-plugin-onlyhtml-connector
```

This will create a folder named sanity-studio where we have our sanity studio project with the OnlyHtml plugin installed. The next step will be to configure Sanity and OnlyHtml, first edit`<your-site>/sanity-studio/sanity.json`and **put an empty array in the `parts` field**. This is important to allow OnlyHtml to control the studio's structure. 

The final file should look like this

```javascript
{
  "root": true,
  "parts": [],
  
  "project": {
    "name": "..."
  },
  "api": {
    "projectId": "xxxxxxxx",
    "dataset": "production"
  },
  "plugins": [
    "@sanity/base",
    "@sanity/components",
    "@sanity/default-layout",
    "@sanity/default-login",
    "@sanity/desk-tool",
    "@onlyhtml/sanity-plugin-onlyhtml-connector"
  ],
  "env": {
    "development": {
      "plugins": [
        "@sanity/vision"
      ]
    }
  }
}
```

Then we need to configure OnlyHtml, open `<your-site>/onlyhtml.json`

```text
{
    "hidden_sections": [],
    
    # add all below this
    "sanity": {
        "projectId": "xxxxxxxx",
        "dataset": "production",
        "useCdn": true,
        "apiVersion": "2021-08-09"
    }
}
```

After doing so we can fire up our new CMS dashboard by running

```bash
# export onlyhtml schema into sanity studio
onlyhtml export sanity \
  --path anity-studio/config/@onlyhtml/sanity-plugin-onlyhtml-connector.json

# fireup the sanity studio dev server
cd ./sanity-studio
sanity start
```

Visit `localhost:3333` to view and edit your website's content. When ready, you can run `sanity deploy` to deploy the dashboard publicly. 

## Sanity

Sanity.io is a headless CMS providing a unified content platform. It is very developer friendly and allows defining schemas and data types directly from code.

### Sanity Studio

The Sanity Studio is an open-source CMS built with React.js. It offers rapid configuration and free form customization. A developer can spin one up locally and when ready deploy the studio to production so non-technical users can use it too. 

Main features include

* Document revision history with rollback to editing sessions.
* Real-time collaboration. No locking or overwriting.
* Works on your phone and other touch devices.
* Batch image uploads. Paste pictures right from the clipboard.
* Large ecosystem of plugins

While developing, sanity studio runs locally in its own process, auto-reloading on any code or configuration change. Running `npm run serve` will start two servers, one for sanity Studio and the other for OnlyHtml. **Edit the content in Sanity Studio and it will automaticlly appear in the website preview.**

When your website is ready for publishing, run sanity deploy and follow the instructions from the sanity tool. This will deploy the Sanity Studio to a publicly available domain so anyone with credentials will be able to edit the content of your new website. 

