# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Surge proxy configuration repository containing network traffic routing rules and automation scripts for the Surge proxy application (macOS/iOS network debugging/filtering tool).

## Repository Structure

- **`rules/`** - Network routing rule lists (`.list` files)
  - `rules/app/` - Application-specific rules (Apple, YouTube, Netflix, Steam, etc.)
  - `web3.list` - Web3/crypto exchange domains
  - `block.list` - Domains to block
- **`modules/`** - Surge module scripts (`.sgmodule` files with associated `.js` scripts)

## File Formats

### Rule Lists (`.list` files)
Two-part comma-separated format: `TYPE,VALUE`

```
DOMAIN-SUFFIX,apple.com
DOMAIN,example.com
DOMAIN-KEYWORD,google
IP-CIDR,192.168.0.0/16
USER-AGENT,*WeChat*
PROCESS-NAME,Telegram
```

**Important**: Rule lists must have exactly two parts. If there's content after VALUE, it's invalid and should be removed.

### Surge Modules (`.sgmodule` files)
INI-style format with `[Section]` segments:
- `[General]` - Key-value settings
- `[Script]` - JavaScript script definitions
- `[URL Rewrite]` - URL rewriting rules
- `[Header Rewrite]` - HTTP header modifications
- `[MITM]` - Man-in-the-Middle hostname configuration (use `%APPEND%` to avoid overwriting other modules' hostnames)

## Common Tasks

**Adding a new rule**: Add a line to the appropriate `.list` file in `rules/` or `rules/app/`

**Creating a new module**: Create a `.sgmodule` file in `modules/` with appropriate sections; if JavaScript is needed, add corresponding `.js` file

## Module Troubleshooting

If a script doesn't work after enabling:
1. Check if other scripts overwrite hostnames (use `%APPEND%` in hostname declarations)
2. Check for `hostname-disabled` in your Surge configuration
