# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `npm install` - Install dependencies
- `npm start` - Start the Discord bot (runs `node app.js`)
- `npm run dev` - Start with nodemon for development (auto-restart on changes)
- `npm run register` - Register slash commands with Discord (runs `commands.js`)

## Architecture Overview

This is a Discord bot example app implementing a rock-paper-scissors-style game with an extended set of choices (rock, paper, scissors, cowboy, wumpus, virus, computer). The app demonstrates Discord's interaction system using slash commands and message components.

### Core Files Structure

- **`app.js`** - Main Express server handling Discord interactions via `/interactions` endpoint
- **`commands.js`** - Slash command definitions and registration utility (run with `npm run register`)
- **`game.js`** - Game logic containing RPS choices, win conditions, and result formatting
- **`utils.js`** - Utility functions including Discord API requests and helper functions
- **`examples/`** - Complete implementations showing different Discord features (buttons, modals, select menus)

### Key Architecture Patterns

**Interaction Handling**: The app uses Express with `discord-interactions` middleware to verify and handle Discord webhook requests. All interactions are processed through the `/interactions` POST endpoint.

**Game State**: Active games are stored in memory using `activeGames` object (keyed by game ID). In production, this should use a database.

**Command Registration**: Slash commands are defined in `commands.js` and registered globally via Discord API using the `InstallGlobalCommands` utility.

**Game Logic**: Extended rock-paper-scissors with 7 choices, each having unique win conditions and flavor text defined in the `RPSChoices` object in `game.js`.

### Environment Setup

Requires `.env` file with:
- `APP_ID` - Discord application ID
- `DISCORD_TOKEN` - Bot token
- `PUBLIC_KEY` - Application public key for request verification

### Discord Integration

The app expects to receive Discord interactions via webhook. For local development, use ngrok or similar to tunnel `localhost:3000/interactions` to a public URL, then configure this URL in the Discord Developer Portal.

### Examples Directory

Contains feature-specific implementations:
- `examples/app.js` - Complete app with full RPS game functionality
- `examples/button.js` - Button component examples
- `examples/modal.js` - Modal interaction examples
- `examples/selectMenu.js` - Select menu component examples