# Private(well,at first I wanted to make it then changed the plan) SearXNG Search Engine

[![Docker](https://img.shields.io/badge/Docker-Ready-blue?logo=docker)](https://www.docker.com/)
[![License](https://img.shields.io/badge/License-AGPL--3.0-green.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![SearXNG](https://img.shields.io/badge/Powered%20by-SearXNG-orange)](https://github.com/searxng/searxng)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](#)

> A self-hosted, privacy-respecting metasearch engine.  
> Aggregates results from multiple search providers without tracking, profiling, or ads.

**Live Demo**: *[Add your public URL here if available]*  
**Author**: Farihatul Maria ([@farihatulmaria](https://github.com/farihatulmaria/))

---

## Overview

This project deploys a fully private instance of [SearXNG](https://github.com/searxng/searxng), an open-source metasearch engine. Unlike commercial search engines, it:

- Does **not** track users or build profiles
- Does **not** serve advertisements
- Queries multiple upstream engines (Google, Bing, DuckDuckGo, Wikipedia, etc.) on the user's behalf
- Strips tracking parameters and can proxy images
- Gives the operator complete control over logging, engines, and data

It is designed as both a practical privacy tool and a learning project in **containerization, configuration management, reverse proxying, and privacy-by-design architecture**.

This repository contains a clean, production-ready Docker Compose setup with sensible defaults, clear documentation, and easy customization - suitable for local use on Windows or deployment to a VPS / PaaS with a custom domain.

---

## Key Features

| Feature                  | Description                                      |
|--------------------------|--------------------------------------------------|
| Privacy-first            | No user tracking, random browser profiles per request, optional image proxy |
| Multi-engine aggregation | Combines & deduplicates results from dozens of sources |
| Fully self-hosted        | You control the instance, logs, and configuration |
| Docker-based             | One-command deployment on Windows, Linux, or macOS |
| Highly configurable      | Engines, themes, safe search, rate limiting, etc. |
| Custom domain support    | Easy integration with domains managed via Vercel or any registrar |
| Lightweight              | Runs well on modest hardware (even a Raspberry Pi or free-tier VPS) |

---

## Architecture

User Browser 
↓ 
SearXNG (this instance) 
↓ 
(parallel anonymous requests) Multiple Search Engines (Google, Bing, DDG, Brave, Wikipedia ...) 
↓ 
Results merged, ranked, cleaned → returned to user

---

## Repository Structure

 ├── core-config/ 
 │      └── settings.yml # Main SearXNG configuration (customize here) 
 ├── docker-compose.yml # Official-based Compose file 
 ├── .env.example # Environment variable template 
 ├── .gitignore 
 └── README.md # You are here

---

- SearXNG never forwards cookies or personal identifiers.
- Upstream engines only see the IP of your server (or your machine if running locally).
- Optional Valkey (Redis-compatible) for caching and rate limiting.
- Configuration is declarative via `settings.yml`.

---

## Tech Stack

- **Application**: [SearXNG](https://github.com/searxng/searxng) (Python)
- **Containerization**: Docker + Docker Compose
- **Cache / Limiter**: Valkey
- **Configuration**: YAML + environment variables
- **Optional**: Caddy / Nginx / Traefik for HTTPS and reverse proxy
- **Platform**: Works on Windows (Docker Desktop + WSL2), Linux, macOS

---

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Windows/macOS) or Docker Engine + Compose (Linux)
- Git
- Basic familiarity with the terminal
- (Optional) A domain name (can be managed through Vercel, which I did)

