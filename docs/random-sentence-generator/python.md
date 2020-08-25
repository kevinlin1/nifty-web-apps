---
title: Nifty Web Apps
---

# Random Sentence Generator

Run the console app with `python3 generator.py`. When prompted for a target, try entering `SENTENCE`. If everything goes well, you should see the following output appear.

```
Valid symbols: SENTENCE NOUNP PROPNOUN ADJS ADJ DET NOUN VERBP TRANSVERB INTRANSVERB
Target: SENTENCE
the big child hit a big man
John laughed
the pretentious dog laughed
Elmo kissed Jane
the big mother laughed
the faulty wonderful man died
Jane laughed
the pretentious faulty wonderful subliminal man hit Spot
Sally laughed
a subliminal big father helped Sally

Target:
```

## Modify the web app

Now, let's fill in step 1 and 2 for the Random Sentence Generator. This app should generate English sentences when given the target `SENTENCE`. **Modify the `server.py` file to implement step 1 and 2.**

Note
: For step 2, call [`random.sample`](https://docs.python.org/3/library/random.html#random.sample) to pick one random element from a set of elements.

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
  <input type="text" value="SENTENCE" disabled>
  <div>
    <p>the big child hit a big man</p>
    <p>John laughed</p>
    <p>the pretentious dog laughed</p>
    <p>Elmo kissed Jane</p>
    <p>the big mother laughed</p>
    <p>the faulty wonderful man died</p>
    <p>Jane laughed</p>
    <p>the pretentious faulty wonderful subliminal man hit Spot</p>
    <p>Sally laughed</p>
    <p>a subliminal big father helped Sally</p>
  </div>
</body>
</html>
{% endcapture %}
<iframe srcdoc='{{ srcdoc }}' style='border: none; height: 526px; max-width: 600px; width: 100%;'></iframe>

Then, try clicking on the ⚡ (lightning bolt) icon and see what happens.

When you're done demoing the web app, stop the Python terminal process with <kbd>Ctrl+C</kbd>.
