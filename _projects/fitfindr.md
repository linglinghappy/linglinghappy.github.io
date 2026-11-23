---
layout: page
title: FitFindr AI Shopping Agent
description: LLM agent that finds thrift listings through an MCP tool and styles them with your wardrobe, served as a cached Flask API.
img: assets/img/projects/fitfindr.jpg
importance: 2
category: ai
github: https://github.com/linglinghappy/fitfindr-agent
skills: [Python, LLM Agents, MCP, Gemini API, Flask, Evaluation]
---

**Code:** [GitHub](https://github.com/linglinghappy/fitfindr-agent){:target="\_blank"} · **Full engineering report:** [course-report.md](https://github.com/linglinghappy/fitfindr-agent/blob/main/docs/course-report.md){:target="\_blank"}

{% include figure.liquid path="assets/img/projects/fitfindr_architecture.svg" class="img-fluid rounded z-depth-1" alt="FitFindr architecture: Flask serving layer with a response cache in front of a five-step agent that calls an MCP server and the Gemini API" avoid_scaling=true %}

<div class="caption">Blue boxes are what I implemented; the gray box came from the course starter.</div>

Describe what you want, like _"vintage graphic tee under $30"_, and FitFindr searches thrift listings, picks the best match, suggests outfits using clothes you already own, and writes a short caption you could post about the find.

## How it works

1. **Parse** the request into keywords, size, and maximum price with regular expressions (no model call)
2. **Search** 40 listings through an **MCP tool**, scored by keyword match with size and price filters
3. **Branch:** if nothing matches, stop and tell the user what to change instead of calling the model
4. **Suggest outfits** with Gemini, using pieces from the user's wardrobe
5. **Write a caption** with Gemini that names the item, price, and platform

## What I built

- **Agent:** query parser, planning loop with an empty-result branch, and all three tools
- **MCP:** registered the search tool on the MCP server, with a direct-call fallback
- **Evaluation:** wrote acceptance criteria first, then ran each one several times before and after every change
- **Serving:** response cache (TTL + LRU), a structured log record for every request, per-stage latency timing, and a token-protected logs route
- **Reliability:** retry with backoff for Gemini `503` errors, with a test that proves it
- **Deployment:** Flask with Gunicorn on Render

## Results

|                       | Uncached run    | Cache hit |
| --------------------- | --------------- | --------- |
| Latency (server side) | 2,172 ms median | ~1 ms     |
| Model calls           | 2               | 0         |
| Tokens                | ~576            | 0         |

- **Reliability:** the first deployed test missed two of five criteria because a temporary Gemini `503` wasn't retried. After the fix, all five criteria were met in all three trials.
- **Prompt fix:** 19 of 25 captions were over 300 characters (up to 406). One added instruction brought that to 0 of 25, with every other criterion still passing.
- **Known limitation:** keyword scoring can rank a black plaid shirt above black boots for _"black combat boots"_. The report explains why and how I'd fix it.

## Tech stack

Python · Google Gemini API · Model Context Protocol (MCP) · Flask · Gunicorn · Render

## Acknowledgement

Built as the final project for [CodePath](https://www.codepath.org/){:target="\_blank"} **AI201: Applications of AI Engineering** (Fall 2026). The course provided a starter repository with the CLI, the listings dataset, the Flask route skeleton, the Gemini client, and the MCP scaffolding. I implemented the agent, its tools, the evaluation, the deployment, and the production improvements.
