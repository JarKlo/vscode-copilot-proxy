# Webview Status Panel

## Overview

Replace the busy modal dialog with a clean, styled Webview panel that displays server status, models, and endpoints in a visually appealing way.

## Design Approach

Use `vscode.window.createWebviewPanel()` to create an on-demand panel that opens when user clicks the status bar or runs the status command. This mirrors the original UX but with rich HTML/CSS styling.

## Visual Design

- Clean card-based layout
- Status indicator with color (green when running, gray when stopped)
- Models displayed in individual cards
- Endpoints with copy-to-clipboard buttons
- Start/Stop button integrated in panel
- Minimal, modern aesthetic using VS Code's theme variables

## Architecture

### Components

```
┌─────────────────────────────────────┐
│  Copilot Proxy                      │
├─────────────────────────────────────┤
│  ● Running on port 4141    [Stop]   │
│  ○ Stopped                 [Start]  │
├─────────────────────────────────────┤
│  Models (3)                         │
│  ┌─────────────────────────────────┐│
│  │ GPT-4o                          ││
│  │ copilot:gpt-4o - microsoft      ││
│  │ Family: gpt-4o | Max: 128,000   ││
│  └─────────────────────────────────┘│
├─────────────────────────────────────┤
│  Endpoints                          │
│  POST /v1/chat/completions    [📋] │
│  GET  /v1/models              [📋] │
│  GET  /health                 [📋] │
└─────────────────────────────────────┘
```

### Message Protocol

Communication between webview and extension:

```typescript
// Webview -> Extension
{ command: 'start' }
{ command: 'stop' }
{ command: 'copy', text: string }

// Extension -> Webview (via HTML regeneration)
Panel content is regenerated with current state
```

### Key Functions

- `getWebviewContent(isRunning, port, models)` - Generates HTML/CSS/JS for panel
- `showStatus()` - Creates or reveals the webview panel
- `updateStatusPanel()` - Refreshes panel content when state changes
- `escapeHtml(text)` - Prevents XSS in dynamic content

## CSS Theme Integration

Uses VS Code CSS variables for seamless theme support:

- `--vscode-editor-background`
- `--vscode-foreground`
- `--vscode-button-background`
- `--vscode-button-foreground`
- `--vscode-button-hoverBackground`
- `--vscode-editor-inactiveSelectionBackground`
- `--vscode-focusBorder`
- `--vscode-descriptionForeground`
- `--vscode-textLink-foreground`
- `--vscode-widget-border`
- `--vscode-toolbar-hoverBackground`

## Files Modified

- `src/extension.ts` - Added webview panel implementation

## Implementation Notes

- Panel is singleton - clicking status bar reveals existing panel or creates new one
- Panel automatically updates when server starts/stops
- Copy buttons use native clipboard API with fallback to extension messaging
- Panel is disposed on extension deactivation
