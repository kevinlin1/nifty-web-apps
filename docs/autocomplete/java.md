---
title: Nifty Web Apps
---

# Autocomplete

Run the console app with `javac Autocomplete.java && java Autocomplete`. When prompted for a query, try entering "Sea". If everything goes well, you should see the following output appear.

```
Query: Sea
608660 Seattle, Washington, United States
33025 Seaside, California, United States
26909 SeaTac, Washington, United States
24168 Seal Beach, California, United States
22858 Searcy, Arkansas, United States

Query:
```

## Run the web app

Run the web app with `javac Server.java && java Server`. In a web browser, navigate the following address: `localhost:8000`.

{% capture srcdoc %}
<!DOCTYPE html>
<html>
<head>
  <style>
    * {
        box-sizing: border-box;
    }
    *:focus {
        outline: 0;
    }
    form {
        position: relative;
    }
    button {
        background: none;
        border: none;
        font-size: 1.5rem;
        position: absolute;
        right: 0;
        top: 0.5em;
    }
    p, input {
        color: #444;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        font-size: 1.25rem;
        line-height: 1.5;
        margin: 0;
        overflow: hidden;
        padding: 0.5rem 1rem;
        text-overflow: ellipsis;
        user-select: none;
        white-space: nowrap;
        width: 100%;
    }
  </style>
</head>
<body>
  <form>
    <button disabled>⚡</button>
  </form>
  <input type="text" value="Sea" disabled>
  <div>
    <p>Seattle, Washington, United States</p>
    <p>Seaside, California, United States</p>
    <p>SeaTac, Washington, United States</p>
    <p>Seal Beach, California, United States</p>
    <p>Searcy, Arkansas, United States</p>
  </div>
</body>
</html>
{% endcapture %}
<iframe srcdoc='{{ srcdoc }}' style='border: none; height: 296px; max-width: 600px; width: 100%;'></iframe>

When you're done demoing the web app, stop the Java terminal process with <kbd>Ctrl+C</kbd>.

## Modify the web app

Now that we know how to change the logic for the backend web server, let's explore the frontend of the Autocomplete web app, which automatically suggests cities that start with the same name as the given query string. We'll learn how to modify the `Server.java` file and the `index.html` file to display not only the name of the city, but also its weight (e.g. population).

**Our goal is to modify the app and display the weight as a right-aligned, gray number.** By the time we're done, our web app should look like the following.

{% capture srcdoc %}
<!DOCTYPE html>
<html>
<head>
  <style>
    * {
        box-sizing: border-box;
    }
    *:focus {
        outline: 0;
    }
    form {
        position: relative;
    }
    button {
        background: none;
        border: none;
        font-size: 1.5rem;
        position: absolute;
        right: 0;
        top: 0.5em;
    }
    p, input {
        color: #444;
        font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        font-size: 1.25rem;
        line-height: 1.5;
        margin: 0;
        overflow: hidden;
        padding: 0.5rem 1rem;
        text-overflow: ellipsis;
        user-select: none;
        white-space: nowrap;
        width: 100%;
    }
    p span {
        color: #888;
        float: right;
    }
  </style>
</head>
<body>
  <input type="text" value="Sea" disabled>
  <div>
    <p>Seattle, Washington, United States<span>608660</span></p>
    <p>Seaside, California, United States<span>33025</span></p>
    <p>SeaTac, Washington, United States<span>26909</span></p>
    <p>Seal Beach, California, United States<span>24168</span></p>
    <p>Searcy, Arkansas, United States<span>22858</span></p>
  </div>
</body>
</html>
{% endcapture %}
<iframe srcdoc='{{ srcdoc }}' style='border: none; height: 296px; max-width: 600px; width: 100%;'></iframe>

### Sending JSON objects

Currently, our app calls `send` with a `{"items": result}`, where `result` is a list of strings. This works fine if we only want to display a list of strings in the same, consistent style. But we want to differentiate between the name of the city and its weight.

**Modify the code in `Server.java` so that the result is a list with the following structure.**

```python
result = [
    {"query": "Seattle, Washington, United States",
     "weight": 608660},
    {"query": "Seaside, California, United States",
     "weight": 33025},
    ...
]
```

### Rendering JSON objects

By modifying the format of the result that's sent to the frontend, we've changed the **API** (application programming interface) of the web app. Any program using the `Server.java` needs to be updated to handle the JSON objects; they can no longer just display each result as a string.

Let's take a look at `index.html`. This is a complicated file, with many historical reasons behind its peculiar formatting, but let's focus on what we need to do to get our web app working again and displaying results.

**Find the template tag** starting in `<template type="amp-mustache">` and ending in `</template>`. This template is used to render each result in the list of results. It tells the browser to loop over each result and display it as a paragraph with the paragraph tag: `{% raw %}<p>{{.}}</p>{% endraw %}`. The special code `{% raw %}{{.}}{% endraw %}` represents the part of the template that will be substituted with the real string data.

`.` (period) represents the entire element. This worked when the entire element was just a string. But now, each element has two keys: `query` and `weight`. **Modify the template tag to display the query and weight.** (The weight will be formatted with a nested **span tag**, representing a specially-formatted substring in the paragraph.)

```html
{% raw %}<p>{{query}}<span>{{weight}}</span></p>{% endraw %}
```

### CSS (Cascading Style Sheets)

This works to display the results again, but we want to display it aligned to the right with a gray font color. We'll need to look at a different part of the `index.html` file that's responsible for specifying the appearance of the web app.

**Find the style tag** starting in `<style amp-custom>` and ending in `</style>`. Websites are styled in a different language called CSS. At the bottom of the style tag, add the following style. This style states the appearance of a span tag nested within a paragraph tag should appear as slightly light gray and float in the right side of its container (the paragraph tag).

```css
p span {
  color: #888;
  float: right;
}
```

### Remove unused code

There's no need for a ⚡ (lightning bolt) button, so we should make sure to remove its API endpoint in the `Server.java` file and the corresponding `form` and `button` elements from the `index.html` file. Since there are no other `form` or `button` elements, we can also remove the `form` and `button` styles. There's also one more tag that we can remove: the `script` import tag for `amp-form`.
