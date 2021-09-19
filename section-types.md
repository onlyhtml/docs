# Section Types

### Section

By default, OnlyHtml places fields into the a section called "General" in your dashboard. After a while, though, this can become unwieldy.

Sections are an organizational unit of OnlyHtml. They allow you to group tags together, and display them under a separate dashboard page, other than General.

To create a section, just enclose template tags within a section block:

```text
{{#section about}}
<div>
  <h2>{{ic title}}</h2>
  {{ic body type="html"}}
</div>
{{/section}}
```

### Collection

Occasionally, you’ll want to create a section that has repeating content, this is what `Collection` is for. For example, let’s say you want to give the ability to edit company office locations:

```text
<ul>
  {{#collection offices}}
    <li>
      <h5>{{name}}</h5>
      {{city}}, {{state}}
    </li>
  {{/collection}}
</ul>
```

### Collection Item

Some collections require an overview page and a details page. Continuing the example above, we might want to create individual page for each office. For this, we can use the `{{_permalink}}` template tag \(note the underscore before “permalink”\).

```text
<ul>
  {{#collection offices multiple=true}}
    <li>
      <h5><a href="{{_permalink}}">{{ic name}}</a></h5>
      {{ic city}}, {{ic state}}
    </li>
  {{/collection}}
</ul>
```

The `{{_permalink}}` tag tells OnlyHtml to create a link for this individual office. When the link is clicked OnlyHtml will render a template file at `www/<collection-name>.html`. In our example OnlyHtml will look for a file named `www/_offices.html` . Here is an example for a details page for our office. 

```text
<body>
{{#collection_item}}
    <h1>{{ic title}}</h1>
    {{ic body type="html"}}
{{/collection_item}}
</body>
```

Notice how we used `collection-item` to render a specific item in our collection. 

### Page

Page is technically the same as a section, the only difference depends on the dashboard support. The target is to allow different areas in the dashboard for full pages and sections. For example I would use {{\#page}} for a section that is tied directly to the speicifc page, but use a section for a Contact Us section that might appear in the end of each page and is not tied to a specific page. 

