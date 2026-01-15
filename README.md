# Portfolio Engine 🚀

A minimal, high-performance static site generator pipeline backed by a private Obsidian Vault.

This repository serves as the Presentation Layer (Engine) for my personal portfolio. It is decoupled from the Content Layer (Data), which resides in a private secure repository.

## Architecture

The platform follows a Headless CMS pattern using Git as the single source of truth.

![alt text](image.png)

- Engine: Hugo (Static Site Generator) using the `PaperMod` theme.

- Content: Private Obsidian Markdown files.

- Pipeline: GitHub Actions to pick events from the private repository and trigger deployment.

- Hosting: GitHub Pages

## 🛠 Prerequisites

- Hugo: v0.146.0+ (Extended Edition)

- Git

- Obsidian (for content creation)

## 🚀 Quick Start (Local Development)

**Clone the Repo:**

```bash
git clone --recurse-submodules https://github.com/NewerKey/portfolio-engine.git
```

**Install Dependencies:** If you didn't use --recurse-submodules, pull the theme:

```bash
git submodule update --init --recursive
```

## Run the Server

`hugo server -D`

## Config & Secrets

Create a Personal Access Token allowing the Engine to pull from the Private Vault and push to gh-pages.

Get token here --> [Personal Access Token](https://github.com/settings/tokens) --> Scope: repo, workflow --> save in both private and public repo settings under secrets as below

```bash
PAT_TOKEN
```

## 📝 Publishing Workflow

You can then manage your content within Obsidian locally or private repo.

1. Write: Create a note in your private Obsidian vault.

2. Flag: Add the following Frontmatter to any note you wish to publish:

```bash
---
title: "My New Post"
date: 2026-01-01
publish: true  <-- The Workflow Trigger Switch
---
```

- Push: Commit and push your Obsidian vault (or use the Obsidian Git plugin).

- Deploy: The pipeline automatically triggers, filters only publish: true files, converts WikiLinks, and deploys.

## 🎨 Customization

- Theme Config: hugo.toml (Adjust menus, profile info, social links).

- Styling: assets/css/custom.css (Overrides for typography and layout).

- Layouts: layouts/ (HTML structure overrides).
