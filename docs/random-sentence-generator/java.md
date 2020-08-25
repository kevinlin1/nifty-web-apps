---
title: Nifty Web Apps
---

# Random Sentence Generator

Run the console app with `javac RandomSentenceGenerator.java && java RandomSentenceGenerator`. When prompted for a target, try entering `SENTENCE`. If everything goes well, you should see the following output appear.

```
Valid symbols: SENTENCE NOUNP PROPNOUN ADJS ADJ DET NOUN VERBP TRANSVERB INTRANSVERB
Target: SENTENCE
the faulty pretentious university wept
a big child wept
Elmo collapsed
a big faulty subliminal cat honored Elmo
the pretentious cat collapsed
John laughed
Fred laughed
the green university laughed
the faulty mother helped a wonderful subliminal wonderful subliminal man
Fred helped John

Target:
```

## Modify the web app

Now, let's fill in step 1 and 2 for the Random Sentence Generator. This app should generate English sentences when given the target `SENTENCE`. **Modify the `Server.java` file to implement step 1 and 2.**

Note
: For step 2, call `randomChoice` to pick one random element from a collection of elements.

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
  <input type="text" value="SENTENCE" disabled>
  <div>
    <p>the faulty pretentious university wept</p>
    <p>a big child wept</p>
    <p>Elmo collapsed</p>
    <p>a big faulty subliminal cat honored Elmo</p>
    <p>the pretentious cat collapsed</p>
    <p>John laughed</p>
    <p>Fred laughed</p>
    <p>the green university laughed</p>
    <p>the faulty mother helped a wonderful subliminal wonderful subliminal man</p>
    <p>Fred helped John</p>
  </div>
</body>
</html>
{% endcapture %}
<iframe srcdoc='{{ srcdoc }}' style='border: none; height: 526px; max-width: 600px; width: 100%;'></iframe>

Then, try clicking on the ⚡ (lightning bolt) icon and see what happens.

When you're done demoing the web app, stop the Java terminal process with <kbd>Ctrl+C</kbd>.
