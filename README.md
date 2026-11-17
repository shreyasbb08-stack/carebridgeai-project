# CareBridge AI — Student Health Navigator

CareBridge AI is a student health education and care-navigation prototype. This project can run in development mode or as a standalone Windows desktop application.

## A. Run in VS Code (development)

Requirements: Node.js 20 LTS or newer.

1. Extract this ZIP.
2. In VS Code choose **File → Open Folder** and select the folder that directly contains `package.json`.
3. Open **Terminal → New Terminal**.
4. Run `node -v` and `npm -v`.
5. Run `npm install`.
6. Run `npm run dev`.
7. Open `http://localhost:5173`.

Keep the terminal open while using development mode. Press `Ctrl+C` to stop.

## B. Run as a normal Windows application (no VS Code)

You only need to do these build steps once on a Windows computer:

1. Install Node.js 20 LTS or newer.
2. Extract this project and open its root folder (the folder containing `package.json`) in a terminal. You can use Windows File Explorer: open the folder, click the address bar, type `cmd`, and press Enter.
3. Run:
   ```bash
   npm install
   ```
4. Build the Windows installer:
   ```bash
   npm run dist:win
   ```
5. Wait for the build to finish. Find the installer in the `release` folder:
   `CareBridge-AI-Setup-1.0.1.exe`
6. Double-click the installer, follow the setup wizard, and keep the desktop shortcut selected.
7. After installation, open **CareBridge AI** from the desktop shortcut or Windows Start menu.

After installation, you do not need VS Code, a terminal, or a separately running development server. The desktop app starts its local API server automatically and opens its own window.

To test the desktop app before creating the installer, run:
```bash
npm run desktop
```

## Optional AI configuration

The app works in safe demo mode without an API key. To enable optional AI-generated educational responses:

1. Copy `.env.example` to `.env` in the project root.
2. Add your key:
   ```env
   OPENAI_API_KEY=your_api_key_here
   OPENAI_MODEL=gpt-4o-mini
   PORT=5000
   ```
3. Rebuild/relaunch the app.

Never put the API key in frontend code or a `VITE_` variable. Do not share the `.env` file. API usage may incur charges.

## Troubleshooting

- **ENOENT / cannot find package.json:** You opened the parent folder. Open the folder where `package.json` is directly visible.
- **`npm` is not recognized:** Install Node.js LTS and restart the terminal.
- **Build fails:** Delete `node_modules` and `package-lock.json`, then run `npm install` and `npm run dist:win` again.
- **Windows says the publisher is unknown:** This locally built installer is not code-signed. Only install builds you created or trust.
- **Nearby care search does not work:** It needs an internet connection, location permission, and public OpenStreetMap services.

## Important health and privacy limitations

CareBridge AI is an educational student project, not a medical device, diagnostic system, emergency service, or substitute for professional care. Emergency keyword detection can miss emergencies. In India, call 112 for emergencies. Do not delay urgent care to use this app.

Conversation history and reminders are stored in browser local storage and are not encrypted medical-record storage. Avoid entering sensitive health information, especially on shared computers. Nearby-place data may be incomplete or outdated. The app requires internet access for OpenStreetMap lookups, Google Maps directions, Google Fonts, and optional AI responses.
