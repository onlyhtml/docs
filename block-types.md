# Block Types

## Content Types

By default, OnlyHtml assumes that all template tags are text, and will generate text field inputs in the dashboard. You can easily change the type of dashboard input by specifying one of the types below.

```
{{oh intro type="html"}}
```

Additionally, template tags accept any number of parameters, which can tell OnlyHtml how to render the content, or how to further configure the dashboard input. Each content type below has a corresponding table which describes its parameters.

All types have these common parameters

| Parameter Name | Default Value | Possible Values | Description                                                                                                                    |
| -------------- | ------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| default        |               | any text        | The default value of the field. In [rapid mode ](intergrations/rapid-prototyping.md)will render this value as the fields value |

### Text

Just plain text :)

| Parameter Name | Default Value | Possible Values | Description                                                                                          |
| -------------- | ------------- | --------------- | ---------------------------------------------------------------------------------------------------- |
| words          | 8             | any number      | In [rapid mode,](intergrations/rapid-prototyping.md) will generate random text with the given length |
| sentences      |               | any number      | In [rapid mode](intergrations/rapid-prototyping.md), will generate random text with the given length |

### HTML

| Parameter Name | Default Value | Possible Values | Description                                                                                         |
| -------------- | ------------- | --------------- | --------------------------------------------------------------------------------------------------- |
| class          |               | any text        | Adds a `class` attribute to the parent  `div`                                                       |
| paragraphs     |               | any number      | In [rapid mode](intergrations/rapid-prototyping.md) will generate random text with the given length |

### Image

| Parameter Name | Default Value | Possible Values | Description                                                                                                              |
| -------------- | ------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------ |
| tag            | true          | true \| false   | Render an `img` tag if true, otherwise the src URL.                                                                      |
| class          |               | any text        | Adds `class` attribute to the image                                                                                      |
| style          |               | any text        | Adds `style`attribtue to the image                                                                                       |
| width          |               | any text        | Adds `width`attribute to the image                                                                                       |
| height         |               | any text        | Adds `height`attribute to the image                                                                                      |
| alt TODO       |               | any text        | Adds `alt` attribute to the image                                                                                        |
| lorem\_query   |               | any text        | In [rapid mode](intergrations/rapid-prototyping.md), a query string to fetch a specifc kind of image. For example "dogs" |

### Link

link is an alias to a text field together with a URL field. It will render a an `<a>` tag

| Parameter Name | Default Value | Possible Values | Description                                                                                              |
| -------------- | ------------- | --------------- | -------------------------------------------------------------------------------------------------------- |
| tag            | true          | true \| false   | Render an `a` tag, otherwise the only the URL                                                            |
| onlytext       | false         | true \| false   | Render only the textual value of the link                                                                |
| words          | 2             | any number      | In [rapid mode](intergrations/rapid-prototyping.md) will generate random link text with the given length |
| class          |               | any text        | Add `class` attribute                                                                                    |

### Icon

icon renders an `<i>` tag with automatic font-awesome css classes

| Parameter Name | Default Value | Possible Values | Description           |
| -------------- | ------------- | --------------- | --------------------- |
| class          |               | any text        | Add `class` attribute |

### Video

Video supports videos stored on Sanity.io using mux.com as a backend.

| tag          | true  | true \| false | Render an `video` tag if true, otherwise the src URL.             |
| ------------ | ----- | ------------- | ----------------------------------------------------------------- |
| poster       | image | image \| gif  | What kind of thumbnail should be displayed before video is played |
| controls     |       | any text      | Adds `contorls` attribute to the image                            |
| loop         |       | any text      | Adds `loop`attribtue to the image                                 |
| preload      |       | any text      | Adds `preload` attribute to the image                             |
| playsinline  |       | any text      | Adds `playsinline` attribute to the image                         |
| controlsList |       | any text      | Adds `controlsList` attribute to the image                        |

### Date

| Parameter Name | Default Value | Possible Values                                                                             | Description                             |
| -------------- | ------------- | ------------------------------------------------------------------------------------------- | --------------------------------------- |
| format         | %B %e, %Y     | anything supported by [strftime](https://github.com/samsonjs/strftime#supported-specifiers) | Formats the date                        |
| timezone       | +0000         |                                                                                             | Sets a specific timezone to input field |

### Code Snippet

Raw code snippet to inserted into the page as is. In CMS will be presented in code aware editor.

| Parameter Name | Default Value | Possible Values         | Description                             |
| -------------- | ------------- | ----------------------- | --------------------------------------- |
| language       |               | any known language name | will control syntax highlighting in CMS |

### Choice

Presents the user with a choice, from zero to multiple options. This would typically be used if you were asking for Yes/No answer, to choose one from many options, or in some case multiple-choice.

For example, this code will render "Love It" if the input field is selected and "Hate It" if it is u

```
{{oh my_opinion type="choice" options="Love It,Hate It"}} 
```

Another example where there is only one option. In case the input checkbox is not-selected no value will be rendered.

```
{{oh my_opinion type="choice" options="its-on"}} 
```

| Parameter Name | Default Value | Possible Values             | Description |
| -------------- | ------------- | --------------------------- | ----------- |
| options        |               | comma delimited text values |             |

### Reference

{% hint style="info" %}
This feature is unstable
{% endhint %}

What if we have a a blog where each post has one author. We could set up a field of a post to be the author name and author picture, problem is it feels we are repeating ourselves. Instead we can use reference fields.&#x20;

For example, lets look at this blog post

```html
<main>
    {{#collection_item post}}
       <h1>{{oh title}}</h1>
       
       {{declare author type="reference" target="author"}}
       {{#with author}}
         <span>{{name}}</span>
       {{/with}}

    {{/collection_item}}
</main>
```

| Parameter Name | Default Value | Possible Values     | Description                         |
| -------------- | ------------- | ------------------- | ----------------------------------- |
| target         |               | any collection name | the collection we want to reference |
| multiple       | false         | true \| false       | allow selecting more than one item  |
