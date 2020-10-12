---
title: Nifty Web Apps
---

# Nifty Web Apps

Welcome to the Nifty Web Apps tutorial: **learn how to build a simple web app for any text-based programming assignment** ([arXiv:2010.04671](https://arxiv.org/abs/2010.04671)). All materials are [open source on GitHub](https://github.com/kevinlin1/nifty-web-apps).

*[IDE]: Integrated Development Environment

In this tutorial, we'll **use, modify, and create** ([Lytle et al. 2019](https://doi.org/10.1145/3304221.3319786)) simple web apps that take a string query and return a list of results. We offer the tutorial in two programming languages: Python and Java.

1. **Autocorrect** in [Python](autocorrect/python.md) or [Java](autocorrect/java.md).
1. **Random Sentence Generator** ([Zelenski 1999][]) in [Python](random-sentence-generator/python.md) or [Java](random-sentence-generator/java.md).
1. **Autocomplete** ([Wayne 2016][]) in [Python](autocomplete/python.md) or [Java](autocomplete/java.md).
1. [Build better sites faster with Chrome DevTools](https://youtu.be/VYyQv0CSZOE): use DevTools to inspect the full [Autocomplete web app][].
1. Deploy your app for free in [Python](deploy/python.md) or [Java](deploy/java.md).

[Zelenski 1999]: http://www-cs-faculty.stanford.edu/~zelenski/rsg/
[Wayne 2016]: http://nifty.stanford.edu/2016/wayne-autocomplete-me/
[Autocomplete web app]: https://autocomplete-me.herokuapp.com/

The [Autocomplete web app][] takes a string prefix and displays the list of matches on top of Google Maps. Compare the web app with the desktop app and the console app.

Web app
: ![Autocomplete web app](autocomplete-web.png)

Desktop app ([Wayne 2016][])
: ![Autocomplete desktop app](autocomplete-gui.png)

Console app
: ```
  Query: Sea
  608660 Seattle, Washington, United States
  33025 Seaside, California, United States
  26909 SeaTac, Washington, United States
  24168 Seal Beach, California, United States
  22858 Searcy, Arkansas, United States

  Query:
  ```
