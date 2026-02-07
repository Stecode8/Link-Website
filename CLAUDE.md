# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **TikTok Link Redirect Page** - a simple single-page application designed to help TikTok users open external links in their default browser, bypassing TikTok's in-app browser restrictions.

### Purpose
- Detects if the user is accessing from TikTok's in-app browser
- If TikTok detected: Shows visual instructions to open link in external browser
- If not TikTok: Auto-redirects to the target URL after 500ms

### Target URL
Currently redirects to: `https://beacons.ai/cnmastairs`

## Project Structure

```
Link-Website/
├── index.html          # Main redirect page with TikTok detection
├── .gitignore         # Git ignore rules
└── server.log         # Local development server logs (not tracked)
```

## Development Commands

### Local Development Server
Run from the repository root:

```bash
python3 -m http.server 8000 > server.log 2>&1 & echo $!
```

**Access**: `http://localhost:8000`

### Server Management
```bash
# Check if server is running
ps aux | grep python3 | grep http.server

# View server logs
cat server.log

# Stop the server (replace PID with actual process ID)
kill [PID]
```

## Technical Details

### TikTok Detection
The page detects TikTok's in-app browser by checking for these user agent strings:
- `musical_ly` (TikTok's original codename)
- `trill` (TikTok's international version)
- `JsSdk` (TikTok's JavaScript SDK identifier)

### User Experience Flow
1. **TikTok Users**:
   - See animated instructions with visual cues
   - Menu pointer arrow appears in top-right corner
   - Step-by-step guide to open in external browser

2. **Non-TikTok Users**:
   - Immediate auto-redirect (500ms delay)
   - No manual interaction required

### Styling
- Dark theme with cyan accent color
- Fully responsive mobile-first design
- Smooth animations and transitions
- Optimized for mobile viewing

## Deployment

This page is designed to be deployed as a static site on:
- GitHub Pages
- Netlify
- Vercel
- Any static hosting service

**Important**: Update the `TARGET_URL` constant in the JavaScript (line 368) to change the redirect destination.

## Important Notes
- This is a **static page** - no server-side processing required
- No external dependencies or frameworks
- Self-contained HTML/CSS/JavaScript
- Works offline once loaded
- Mobile-optimized viewport settings
