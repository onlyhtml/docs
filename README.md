# Getting Started

OnlyHtml is a Static Site Generator that helps you build simple websites. It is a companion to Headless CMS systems like [Sanity.io](https://sanity.io), so you get the best experience editing your content while focusing only on the front-end code.

#### OnlyHtml Main Goals

1. You only need to know HTML (plus CSS and JS to the extent that your design calls for it).
2. Avoid designing dashboards and modeling databases
3. Bring your own Headless CMS of choice or use simple markdown files&#x20;

## Running Your First Site

The fastest way to install and get started is to clone one of our templates:

* [https://github.com/onlyhtml/starter-sanity](https://github.com/onlyhtml/starter-sanity)

You can do so by running

```bash
# installing
git clone git@github.com:onlyhtml/starter-sanity.git my-website
cd my-website
npm install

# be ready to fill in some prompts
npm run init

# we are ready, start the server
onlyhtml serve sanity

# in another console, start the local sanity dashboard
cd my-website/sanity-studio
sanity start
```

The first repository will set up a website with OnlyHtml installed ready for fast prototyping but without a dashboard. `starter-sanity` will set up OnlyHtml and connect it to a sanity.io. Read more here [Sanity.io](intergrations/sanity.io.md).

{% embed url="https://youtu.be/oFwXCnnTm1w" %}

### Auto-Generated Sanity.io Dashboard

![](<.gitbook/assets/image (3).png>)

## Publishing

OnlyHtml sites can be deployed to any static hosting provider.

```bash
onlyhtml build  # will output to ./dist
cd dist && surge # use surge.sh to deploy static sites
```
