---
title: Nifty Web Apps
---

# Autocorrect

In this section, we'll learn how to run two versions of an autocorrect app called **Letter Inventory**: a console-based version and a web-based version. We won't be writing any code for this demo!

Prerequisites
: A recent version of [Python 3](https://www.python.org/). We used Python 3.8.5.

First, [download the nifty-web-apps-python repository](https://github.com/kevinlin1/nifty-web-apps-python/archive/master.zip). Unzip the contents.

## Console app

Run the console app with `python3 inventory.py`. When prompted for a query, try entering any word such as "occurence". If everything goes well, you should see the following output appear.

```
Query: occurence
occurrence
concrete
concert
concern
concerned
conference
cancer
soccer
ec
once

Query:
```

## Web app

Run the web app with `python3 server.py`. In a web browser, navigate the following address: `localhost:8000`.

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
  <input type="text" value="occurence" disabled>
  <div>
    <p>occurrence</p>
    <p>concrete</p>
    <p>concert</p>
    <p>concern</p>
    <p>concerned</p>
    <p>conference</p>
    <p>cancer</p>
    <p>soccer</p>
    <p>ec</p>
    <p>once</p>
  </div>
</body>
</html>
{% endcapture %}
<iframe srcdoc='{{ srcdoc }}' style='border: none; height: 526px; max-width: 600px; width: 100%;'></iframe>

Try entering some text in the input text field and see how the app responds. Then, try clicking on the ⚡ (lightning bolt) icon and see what happens.

When you're done demoing the web app, stop the Python terminal process with <kbd>Ctrl+C</kbd>.

## Compare `inventory.py` with `server.py`

When we ran the console app, Python executed the `__main__` code at the bottom of `inventory.py`. When we ran the web app, Python executed the `__main__` code in `server.py`.

Later, we'll adapt this `server.py` file to run a different app called **Random Sentence Generator**. To help make the connections between the console app and the web app, notice how we've marked up matching code snippets: both `server.py` and `inventory.py` contain a comment for `Step 1` and a comment for `Step 2`. These matching code snippets represent the logic that we'll need to change for each assignment.

### `Step 1`: Return the top 10 most similar options

While the `server.py` file adds each option to a running `result` list, the `inventory.py` console app just prints out the result to the screen. This difference is important. `server.py` needs to `self.send` the result back to the web browser as a **JSON string**:

```
{"items": ["occurrence", "concrete", "concert", "concern", ...]}
```

### `Step 2`: Return a random string from the dataset

In addition to entering text directly into the input box, the user can also touch the ⚡ (lightning bolt) icon to randomly fill the input box with a word from the dataset. This is feature is only present in the web app `server.py`. Like step 1, step 2 also needs to `self.send` the result back to the web browser as a JSON string:

```
{"s": "tripadvisor"}
```
