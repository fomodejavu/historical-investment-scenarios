# Security Policy

## Scope

This repository contains **static educational data only** — JSON scenario files, CSV files, Jupyter notebooks, and a standalone HTML widget. There are no servers, APIs, authentication systems, or databases in this repository.

## Reporting a Vulnerability

If you discover a security issue in the **embeddable widget** (`widgets/what-if-widget.html`) — such as an XSS vulnerability — please:

1. **Do not open a public issue**
2. Contact the maintainers via the [fomodejavu.com](https://fomodejavu.com/) website
3. Include a description of the issue and steps to reproduce

We will acknowledge reports within 7 days and aim to patch any valid widget security issues within 30 days.

## Data Integrity

If you believe scenario data has been tampered with or contains deliberate misinformation (rather than an honest data error), please open a **Data Error** issue and flag it as a potential integrity concern.

## Out of Scope

- Speculative future price data (this repo only contains historical data)
- Social engineering
- Physical security
- Issues in third-party dependencies not controlled by this repo
