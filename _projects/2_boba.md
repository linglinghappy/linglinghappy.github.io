---
layout: page
title: Boba Shop Order App
description: Full-stack boba tea ordering app with a live SVG drink preview and full CRUD on Supabase.
img: assets/img/projects/boba.jpg
importance: 2
category: web
github: https://github.com/linglinghappy/boba-shop-order-app
skills: [React, React Router, Supabase, PostgreSQL, SVG]
---

**[View code on GitHub](https://github.com/linglinghappy/boba-shop-order-app){:target="\_blank"}**

{% include figure.liquid path="assets/img/projects/boba.gif" class="img-fluid rounded z-depth-1" alt="Walkthrough" avoid_scaling=true %}

A boba tea ordering app. Users customize a drink, watch a live cup illustration update with every choice, and manage their orders. Orders are stored in a Supabase (PostgreSQL) database with full create, read, update, and delete support.

## Features

- **Drink builder:** choose drink type, sugar level, ice level, and topping
- **Live SVG cup:** tea color follows the drink type, ice cubes follow the ice level, the topping sits at the bottom, and a gauge shows the sugar level
- **Full CRUD with Supabase:** create, view, edit, and delete orders
- **Detail pages:** each order has its own URL with an estimated price, calorie count, and order time
- **Data validation:** database check constraints and Row Level Security on the Supabase table
- **Responsive dark theme** with loading and "not found" states

## Tech Stack

React 19 · Vite · React Router 7 · Supabase (PostgreSQL) · SVG · CSS
