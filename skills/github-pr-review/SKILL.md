---
name: github-pr-review
description: Automatically summarize PR changes and leave structured review comments on GitHub pull requests. Use when reviewing code on GitHub.
---

# GitHub PR Review Helper

Reads the diff of a GitHub pull request, summarizes the changes, and posts a structured review comment.

## Features

- Summarizes added/removed/modified files
- Highlights potential issues
- Posts review comment with suggestions

## Parameters

- **style** (select, optional, default: "concise"): Review style. Options: concise, detailed

## Guidelines

- Read the full diff before generating a summary
- Group changes by file or module for clarity
- Flag potential bugs, security issues, and style violations
- Keep concise reviews under 200 words; detailed reviews can be longer
- Use GitHub's suggestion syntax for concrete code changes
