---
layout: page
title: SJC Flight Dashboard
description: Live flight dashboard for San José Airport with search, filters, charts, and per-flight detail pages.
img: assets/img/projects/sjc.jpg
importance: 3
category: web
github: https://github.com/linglinghappy/sjc-flight-dashboard
skills: [React, React Router, Recharts, REST API, Data Visualization]
---

**[View code on GitHub](https://github.com/linglinghappy/sjc-flight-dashboard){:target="\_blank"}**

{% include figure.liquid path="assets/img/projects/sjc.gif" class="img-fluid rounded z-depth-1" alt="Walkthrough" avoid_scaling=true %}

A live flight dashboard for San José International Airport (SJC), powered by real-time data from the Aviationstack API. Users can browse departures and arrivals, track delays and on-time performance, and open a detail page for any flight.

## Features

- **Live flight data** for SJC departures and arrivals
- **Summary stats:** total flights, on-time rate, delays, and top destinations
- **Search and filter** by flight number, airline, airport, and domestic or international routes
- **Charts:** busiest hours of the day, and average delay for the 8 busiest airlines
- **Flight detail pages** with unique URLs showing terminal, gate, and baggage claim
- **URL-based state:** the Departures / Arrivals tab is stored in the URL, so "Back" returns to the same view
- **API caching** in `localStorage` to stay within the free API limit (100 requests/month)

## Tech Stack

React 19 · Vite · React Router 7 · Recharts · Aviationstack REST API · CSS
