# A TO Z Services — Thisayanvilai

A responsive static website / PWA for a local on-demand services platform (Electrician, Plumber, Mechanic, Driver, FASTag, SIM services, Home Interior, Car & Bike wash, and more) targeting Thisayanvilai. The site includes customer-facing pages (service discovery, map-based location check), a demo customer dashboard, and an admin portal (client-side login).

## Table of contents
- [Overview](#overview)
- [Features](#features)
- [Tech stack](#tech-stack)
- [Repository structure](#repository-structure)
- [How it fits together](#how-it-fits-together)
- [Run locally](#run-locally)
- [Deploy (GitHub Pages)](#deploy-github-pages)
- [Configuration & third-party services](#configuration--third-party-services)
- [Security notes](#security-notes)
- [Contributing](#contributing)
- [Contact](#contact)

## Overview
A TO Z Services is a static frontend (HTML/CSS/JS) offering a simple customer experience to check service availability via PIN or geolocation, view a demo dashboard, and an admin portal to manage access. It also includes PWA manifest and a small service worker (sw.js) indicating intention for offline / installable behavior.

## Features
- Landing page with quick links (Customer / Admin).
- Customer location check using:
  - PIN search (geocoding + map)
  - Browser geolocation (Leaflet map)
- Demo customer dashboard (static UI showcasing services).
- Admin login & admin dashboard (client-side authentication).
- PWA manifest (manifest.json) and a minimal service worker (sw.js).
- Assets (images, icons) for UI and marketing.

## Tech stack
- Languages: HTML, CSS, JavaScript
- Map: Leaflet (CDN)
- Realtime DB (client-side usage): Firebase Realtime Database (compat scripts referenced)
- PWA: manifest.json + sw.js
- No server-side code in this repository (static files only)

## Repository structure
