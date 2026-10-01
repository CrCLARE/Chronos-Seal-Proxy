# Chronos Seal Proxy

> Zero-knowledge "Blind Proxy" OAuth Token exchange relay server — providing OAuth Token exchange services for the Chronos Seal GUI.

## 🛡️ Core Security Principles

This server is the OAuth authorization relay for the Chronos Seal GUI (desktop client). Its sole purpose is to **exchange the GitHub authorization code for an access_token**. It is designed to be an extremely "blind proxy" to ensure the ultimate security of users.

### What we absolutely do NOT do:
1. **Absolutely no data storage**: No database, no logging. The Vercel Serverless function is destroyed immediately after execution.
2. **Absolutely no access to user seeds**: The user's Master Seed is generated entirely locally in the GUI and written directly into the user's own GitHub Secrets.
3. **Absolutely no access to private repositories**: The GitHub App permissions are strictly limited to the user's own forked template repository.

### Data Flow:
`Local GUI` -> `Trigger Browser Authorization` -> `Local GUI captures code` -> `This Server (exchanges for Token)` -> `Local GUI uses Token to directly access GitHub API`

## 🚀 Deployment Guide

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FCrCLARE%2FChronos-Seal-Proxy)

### Environment Variable Configuration:
Add the following in your Vercel project's `Settings -> Environment Variables`:
- `GITHUB_CLIENT_ID`: Your GitHub App Client ID
- `GITHUB_CLIENT_SECRET`: Your GitHub App Client Secret

## 📄 License
This project is open-sourced under the MIT License.

> Don't trust, verify. The source code is here, and security review is always welcome.
