# Rapid Prototyping

The rapid prototyping back-end helps designing websites without worrying about the content. When you like the look of the website you can switch to a different back-end and start filling up actual meaningful content. Getting started with a rapid prototyping back-end is simple, just run:

```
git clone https://github.com/onlyhtml/starter-vanila.git
cd starter-vanila
npm install

# start the servers
onlyhtml serve rapid
```

This will start a server with a "lorem-ipsum" backend, it detects which fields are in each page and generates random content to fill the page. Images will be filled up with random images from free image servers.

{% hint style="info" %}
Lorem Ipsum is a piece of text, used by designers to fill a space where the content will eventually sit. It helps show how text will look once a piece of content is finished, during the planning phase.
{% endhint %}

_Building a website in Rapid Prototyping Mode_

{% embed url="https://youtu.be/YJdEDeDvlxo" %}

_An example website run with a rapid prototyping back-end_

![](../.gitbook/assets/image%20%284%29.png)

### Connecting a CMS

When ready, you can connect a headless CMS of our choice. Currently only Sanity.io is supported. To connect sanity make sure `sanity-cli` is installed and run:

```bash
sanity init --output-path ./sanity-studio --template clean

cd sanity-studio
sanity install @onlyhtml/sanity-plugin-onlyhtml-connector
```

This will create a folder named sanity-studio where we have our sanity studio project with the OnlyHtml plugin installed. The next step will be to configure Sanity and OnlyHtml, first edit`<your-site>/sanity-studio/sanity.json`and put an empty array in the `parts` array. This is important to allow OnlyHtml to control the studio's structure. 

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

Visit `localhost:3333` to view and edit your websites content. When ready, you can run `sanity deploy` to deploy the dashboard publicly. 

