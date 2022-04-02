# Built-In Helpers

Helpers allow you to run functions and transformations while the site is generated. For example we can calculate the time to read by combining `divide` and `length_words` functions.&#x20;

```
Time to read {{divide (words_length body) 225}}
```

We can also skip content if a condition happens

```
{{#compare (length body) 1000 operator="<=" }}
  We have a short body!
{{/compare}}
```

### Log

Log makes debugging templates easier, it is ignored when creating the sites output but will create invoke a log in the console.&#x20;

```
{{log "print the current variables" . }}
```

### Split

### Range

### JSON

### Sum

### Subtract

### Divide

### Length

### Pluck

### Compare

### Contains

### @index

