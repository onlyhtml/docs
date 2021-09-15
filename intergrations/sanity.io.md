# Sanity.io

## Getting Started

We have built a starter project to make it super easy creating a new website with a sanity.io backend. Getting a new project up and ready is as simple as

```bash
git clone git@github.com:onlyhtml/starter-sanity.git
cd starter-sanity
npm install
npm run init

# start the servers
npm run serve
```

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

