# Getting Started

OnlyHtml is Static Site Generator that helps you build simple websites. You write the front-end code using handlebars templates and OnlyHtml will handle all the back-end tasks, creating a Dashboard CMS for you and managing rendering and  deployments.

OnlyHtml is a companion to Headless CMS systems like [Sanity.io](https://sanity.io), so you get the best experience editing your content while focusing only on the front-end code

#### OnlyHtml Main Goals

1. It does _most_ of what you need, but probably not everything.
2. You only need to know HTML \(plus CSS and JS to the extent that your design calls for it\).
3. You should be able to learn the basics in a few minutes.
4. Bring your own Headless CMS of choice or use simple markdown files 

## Running Your First Site

The fastest way to insatll and get started is to clone one of our templates:

* [https://github.com/onlyhtml/starter-vanila](https://github.com/onlyhtml/starter-vanila)
* [https://github.com/onlyhtml/starter-sanity](https://github.com/onlyhtml/starter-sanity)

The first will setup a website with OnlyHtml installed, ready for fast prototyping but without and dashboard. Starter-Sanity will setup OnlyHtml and connect it to a sanity.io. Read more here [Sanity.io](intergrations/sanity.io.md).

### Auto-Generated Sanity.io Dashboard

![](.gitbook/assets/image%20%283%29.png)

## Hosting Your Website

OnlyHtml sites can be deployed to any static hosting provider.

```bash
onlyhtml build  # will output to ./dist
cd dist && surge # use surge.sh to deploy static sites
```

