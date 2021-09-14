# Block Types

## Content Types

By default, OnlyHtml assumes that all template tags are text, and will generate text field inputs in the dashboard. You can easily change the type of dashboard input by specifying one of the types below.

```text
{{ic intro type="html"}}
```

Additionally, template tags accept any number of parameters, which can tell Vapid how to render the content, or how to further configure the dashboard input. Each content type below has a corresponding table which describes its parameters.

```text
{{ic intro type="html" editor="markdown" required=false}}
```

All content types have the following parameters unless specified differently below.

| Parameter Name | Default Value | Possible Values | Description | State |
| :--- | :--- | :--- | :--- | :--- |
| help |  | any text | Adds a helper text near the dashboard input field | Not implemented yet |
| default |  | any text | Set a default value | Partially implemented |
| required | true | true \| false | Specify dashboard input is required | Partially implemented |
| priority |  | any number | By default, the dashboard renders fields in the order they appear in the HTML. By specifying the `priority` option, you can change their order to your liking. | TODO |

### Text

Plain text.

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
|  |  |  |  |

### HTML

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| class |  | any text | html classes to add to root html element |

### Image

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| tag | true | true \| false | Render an `img` tag if true, otherwise the src URL. |
| class |  | any text | Adds `class` attribute to the image |
| style |  | any text | Adds `style`attribtue to the image |
| width |  | any text | Adds `width`attribute to the image |
| height |  | any text | Adds `height`attribute to the image |
| alt TODO |  | any text | Adds `alt` attribute to the image |
| lorem\_query |  | any text | In rapid mode, a query string to fetch a specifc kind of image. For example "dogs" |

### Link

link is an alias to a text field together with a URL field. It will render a an `<a>` tag

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| tag | true | true \| false | Render an `a` tag, otherwise the only the URL |

### Icon

icon renders an `<i>` tag with automatic font-awesome css classes

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| class |  | any text | Add `class` attribute |

### Video

not implemented yet... 

### Date

| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| format | %B %e, %Y | anything supported by [strftime](https://github.com/samsonjs/strftime#supported-specifiers) | Formats the date |
| timezone | +0000 |  | Sets a specific timezone to input field |

### Choice

Presents the user with a choice, from zero to multiple options. This would typically be used if you were asking for Yes/No answer, to choose one from many options, or in some case multiple-choice.

For example, this code will render "Love It" if the input field is selected and "Hate It" if it is u

```text
{{ic my_opinion type="choice" options="Love It,Hate It"}} 
```

Another example where there is only one option. In case the input checkbox is not-selected no value will be rendered.

```text
{{ic my_opinion type="choice" options="its-on"}} 
```



| Parameter Name | Default Value | Possible Values | Description |
| :--- | :--- | :--- | :--- |
| options |  | comma delimited text values |  |
|  |  |  |  |

## 

