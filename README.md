# Getting Started

OnlyHtml is Static Site Generator that helps you build simple websites. You write the front-end code using handlebars templates and OnlyHtml will handle all the backend tasks, creating a Dashboard CMS for you and managing rendering and  deployments.

OnlyHtml is a companion to Headless CMS systems like Sanity.io, so you get the best expirience editing your content while focusing only on the front-end code

#### OnlyHtml Main Goals

1. It does _most_ of what you need, but probably not everything.
2. You only need to know HTML \(plus CSS and JS to the extent that your design calls for it\).
3. You should be able to learn the basics in a few minutes.
4. Bring your own Headless CMS of choice or use simple markdown files 

## Installation

```bash
npm install @onlyhtml/onlyhtml
```

Once you’ve installed OnlyHtml, you can create a new website project by using the following terminal command:

```text
onlyhtml init /path/to/project
```

Then, you’ll be able to start the development web server:

```text
cd /path/to/project
onlyhtml serve
```

This will start a server with a "lorem-ipsum" back-end.

{% hint style="info" %}
Lorem Ipsum is a piece of text, used by designers to fill a space where the content will eventually sit. It helps show how text will look once a piece of content is finished, during the planning phase.
{% endhint %}

When ready, we can connect a headless CMS of our choice. Currently only Sanity.io is supported. To connect saniy

```text
onlyhtml init backend sanity
```

This will update the `onlyhtml.json` configuration files and create a new directory called `./sanity-studio`, read more about Sanity Studio here.

After doing so we can fire up our new CMS dashboard by running

```bash
onlyhtml export sanity
cd ./sanity-studio
sanity start
```

Visit `localhost:3333` to view and edit your websites content. When ready, you can run `sanity deploy` to deploy the dashboard publicly. 

## Hosting Your Website

OnlyHtml sites can be deployed to any static hosting provider.

```bash
onlyhtml build  # will output to ./dist
cd dist && surge # use surge.sh to deploy static sites
```

