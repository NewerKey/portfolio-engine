# Portfolio Engine 🚀

A minimal, "Headless" Static Site Generator for Obsidian users.

> Fork this repository to create your own Portfolio.

This repository acts as the Engine. It contains the code, theme, and build pipeline. It is designed to be empty of content on purpose. It pulls its content from a separate, Private GitHub Repository (your Obsidian Vault) during the build process.

## 🛠 Prerequisites

- Hugo: v0.146.0+ (Extended Edition)

- Git

- Obsidian (for content creation)

## Architecture

The platform follows a Headless CMS pattern using Git as the single source of truth.

![alt text](image.png)

- Secure: Your raw notes stay private. Only files marked publish: true are built.

- Automated: Write in Obsidian -> Push -> Live Site updates in 60s.

- Decoupled: You can swap this engine/theme without touching your notes.

## Components

- Engine: Hugo (Static Site Generator) using the `PaperMod` theme.

- Content: Private Obsidian Markdown files.

- Pipeline: GitHub Actions to pick events from the private repository and trigger deployment.

- Hosting: GitHub Pages

## 🚀 How to Use

**Do not clone this directly.** Instead, follow these steps to make it your own.

- Step 1: Fork the Engine

  - Click the Fork button (top right of this page) to create a copy under your own GitHub account.

  - Go to your new repository's Settings -> Pages.

Source: GitHub Actions (or Deploy from a branch -> gh-pages depending on your setup).

- Step 2: Create Your Content Vault

  - Create a new, empty Private Repository on GitHub (e.g., my-obsidian-vault).

  - In Obsidian, create the following folder structure to match the Engine's configuration:

![alt text](image-1.png)

- Step 3: Connect The Public and Private Repos

  - [Personal Access Token](https://github.com/settings/tokens)

  - Go to your Forked Engine Repo -> Settings -> Secrets and variables -> Actions -> New Repo Secret. Do same for the private Repo

```bash
PAT_TOKEN=your_token
```

- Step 4: Configure the Pipeline

  - Open `.github/workflows/sync-and-deploy.yml` in your fork.

  - Update the repository variable with yours.

## ⚙️ Configuration (hugo.toml)

You must update the configuration file to match your details, or the site will break.

- Open `hugo.toml` and change: `baseURL = "https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/"`

- Profile, Name & Logo:

```bash
title = "Your Name"
[params.label]
    icon = "logo.png" # Upload your own logo to /static/ folder
```

- Menu Links: Adjust the [[menu.main]] section if you changed folder names in Obsidian.

## 📝 Writing & Publishing

1. Write normally in Obsidian
2. Publish a specific note by adding this to the top of the file:

```bash
---
title: "My Note Title"
publish: true
---
```

## 🎨 Customization

- Theme Config: Uses [PaperMod](https://github.com/adityatelange/hugo-PaperMod)

- Images: static/

- Styling: assets/css/custom.css (Overrides for typography and layout).

- Layouts: layouts/ (HTML structure overrides).

---

Original "Portfolio Engine" created by [NewerKey](https://github.com/NewerKey).
