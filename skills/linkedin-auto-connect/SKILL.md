---
name: linkedin-auto-connect
description: Auto-send personalized connection requests from LinkedIn search results with customizable message templates. Use when the user wants to bulk-send LinkedIn connection requests.
---

# LinkedIn Smart Connect

Automatically sends personalized connection requests from LinkedIn people search results.

## Features

- Iterates through search results
- Generates personalized messages from a template
- Supports daily send limit

## Parameters

- **message** (string, required): Connection request message template
- **dailyLimit** (number, optional, default: 20): Maximum requests per day

## Guidelines

- Always respect the daily send limit to avoid LinkedIn rate limits
- Personalize each message using the target person's name and headline
- Skip profiles that already have a pending or accepted connection
- Pause between requests to avoid detection
