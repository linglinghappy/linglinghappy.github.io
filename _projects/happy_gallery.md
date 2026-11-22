---
layout: page
title: Happy Gallery
description: Full-stack online art gallery for my oil paintings, with secure posting, image uploads, and a guest book.
img: assets/img/projects/happy_gallery.jpg
importance: 1
category: web
github: https://github.com/linglinghappy/happy-gallery
skills: [React, Supabase, PostgreSQL, Row Level Security, Full-Stack]
---

**[Live demo](https://happy-gallery.onrender.com/){:target="\_blank"} · [View code on GitHub](https://github.com/linglinghappy/happy-gallery){:target="\_blank"}**

{% include figure.liquid path="assets/img/projects/happy_gallery.gif" class="img-fluid rounded z-depth-1" alt="Walkthrough" avoid_scaling=true %}

An online art gallery where visitors exhibit paintings, admire them, and sign a guest book. I built it to show my own oil paintings: each work hangs in a frame on a lit gallery wall with a museum-style label, and you can click a painting to turn it around and read the story on the back.

## Features

- **Exhibit a work:** upload an image or link one by URL, then add the title, year, medium, subject, and story
- **Museum presentation:** choose a frame and a wall color for each painting
- **Turn the painting around:** a 3D flip reveals the story on the back
- **Guest book and "Admire":** comments and upvotes
- **Browse the collection:** search by title, filter by subject, and sort by newest or most admired
- **Edit or remove your own work** with a secret key
- **Light and dark gallery themes**, with keyboard and screen-reader support

## Security Design

The site has no login, so the database is designed to let visitors do only what the app allows:

- **Row Level Security on every table:** the browser can read posts and add comments, but can't update or delete rows directly
- **Hashed secret keys:** edits and deletes go through Supabase RPC functions that check the key with bcrypt; keys live in a table the browser can never read
- **Validation in the database:** length limits, allowed values, and URL format checks
- **Restricted uploads:** images only, 5 MB maximum, no overwriting or deleting from the website
- **Content filtering** for titles, stories, and comments

## Engineering Challenges

- **Keeping the secret key safe:** moved the check from the browser into database functions protected by Row Level Security
- **Phone photos:** resized to 1600px and re-encoded in the browser before upload, which also strips GPS location data (EXIF)
- **Museum feel:** many rounds of iteration on frames, lighting, labels, and wall color

## Tech Stack

React 19 · Vite · React Router 7 · Supabase (PostgreSQL, Storage, RPC) · Render
