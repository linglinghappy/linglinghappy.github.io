---
layout: page
title: Dog Discover
description: Discover random dog breeds from The Dog API, with a ban list that filters out attributes you don't want.
img: assets/img/projects/dog.jpg
importance: 5
category: web
github: https://github.com/linglinghappy/dog-discover
skills: [React, REST API, async/await]
---

**[View code on GitHub](https://github.com/linglinghappy/dog-discover){:target="\_blank"}**

{% include figure.liquid path="assets/img/projects/dog.gif" class="img-fluid rounded z-depth-1" alt="Walkthrough" avoid_scaling=true %}

Each click fetches a random dog from The Dog API. Users can ban any attribute they're not interested in, and banned values never appear again.

## Features

- **Random discovery:** photo, breed, breed group, life span, and origin for each dog
- **Ban list:** click any attribute to ban it, and click a banned item to remove it
- **Smart filtering:** fetches dogs in batches of 10 (up to 5 tries) and returns the first one with no banned attributes
- **"No match" handling** when every result is filtered out
- **Session history** of every dog discovered

## Tech Stack

React 19 · Vite · The Dog API (REST) · CSS
