# Essentials

## Files and Folders

After you’ve installed OnlyHtml, and issued the `vapid init path/to/project` command, you’ll notice that a new folder was created, containing the following:

```text
www/
.gitignore
package.json
onlyhtml.json
```

The `onlyhtml.json` , `.gitignore`, and `package.json` items are largely ignorable for now. But the `www` folder is where the magic happens.

**Anything you place in “www” folder can be served as your website, with two exceptions: files that start with an underscore \(\_\) or period \(.\) are private, and not viewable by visitors.**

This means that you can put _whatever_ you like in the `www` folder. You can start with the example OnlyHtml template, and build your own custom website, or download a free template from the internet, and drop it in there.

## Content Fields

To make your website dynamic \(i.e. to create a custom dashboard\), you add special template tags in your HTML. For example:

```markup
<html>
  <body>
    <h1>Hello, {{ic name}}!</h1>
  </body>
<html>
```

The `{{ic name}}` tag here has special meaning. It tells Vapid that you’d like place dynamic content there, and that you’d like the dashboard to have a text input field called “Name.” You can have as many of these as you like. Just enclose any word with two curly braces and use the `ic` prefix. 

If you’ve ever used Mustache.js or Handlebars.js, this will be very familiar to you as OnlyHtml extends Handlebars.js. OnlyHtml also allows you to pass parameters into template tags. For example, you could set a placeholder on the dashboard input field by writing:

```text
{{name placeholder="e.g. Tom Waits"}}
```

Or specify that the input is not required \(inputs are required by default\).

```text
{{name placeholder="e.g. Tom Waits" required=false}}
```

One of the more useful parameters you can pass in is called `type`, which lets you change the type of input field you present to the dashboard user. For example, let’s say you wanted to give the ability to add HTML. `{{intro type="html"}}` would display a rich text editor.

There’s no need to get bogged down in the details of all field possibilities right now. You can reference them later in the [Content Types](block-types.md) section. For now, just understand that they help you:   
1\) render content on the front-end; and   
2\) specify what inputs the user will see in the dashboard.

{% hint style="info" %}
You can also use template tags in RSS, XML, and JSON files to create RSS/JSON feeds and sitemaps.
{% endhint %}

## Organizing Content into Sections

As you start adding tags to your website, you’ll probably want to organize how inputs are grouped in the dashboard. For example, you may want to separate fields for the About Us page from welcome message. To do this, you can use `#section` and `#page` tags.

```markup
<h1>Hello, {{ic name}}</h1>

{{#section about}}
<div>
  <h2>{{ic title}}</h2>
  {{ic body type="html"}}
</div>
{{/section}}
```

The `{{#section}}{{/section}}` tags that surround `{{title}}` and `{{body}}` tell OnlyHtml that they should be place into their own group, and have their own page on the dashboard.

What if we want to have repeating content? For that we have `collection`.  
For example, let’s say you want to give the ability to edit company office locations:

```markup
<ul>
  {{#collection offices}}
    <li>
      <h5>{{ic name}}</h5>
      {{ic city}}, {{ic state}}
    </li>
  {{/collection}}
</ul>
```

In this case, the dashboard will give the user the ability to enter _multiple_ office locations, and the front-end will render them as a list.



