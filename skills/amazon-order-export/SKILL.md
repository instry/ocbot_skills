---
name: amazon-order-export
description: Automatically export your Amazon order history to a spreadsheet, with date range filtering. Use when the user wants to scrape or download their Amazon orders.
---

# Amazon Order Export

Scrapes your Amazon order history page, extracts order details (item name, price, date, status), and exports them as a downloadable spreadsheet.

## How to Use

1. Navigate to your Amazon order history
2. Run this skill
3. Wait for automatic pagination
4. Download the generated spreadsheet

## Parameters

- **pages** (number, optional, default: 5): Number of pages to export
- **year** (select, optional, default: "2025"): Order year to export. Options: 2025, 2024, 2023

## Guidelines

- Respects pagination — waits for each page to load before scraping
- Extracts: item name, price, order date, delivery status, order ID
- Outputs a clean spreadsheet with one row per item
- Handles multi-item orders by expanding each item into its own row
