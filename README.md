# Puzzle Studio

A self-contained, free collection of 29 puzzle games: Number Puzzle, Photo Puzzle, Memory Match, Jigsaw, 2048, Lights Out, Word Search, Sudoku, KenKen, Nonogram, Minesweeper, Color Sort, Tower of Hanoi, Mastermind, Peg Solitaire, Pipe Connect, Queens, Unblock, Tic-Tac-Toe, Connect Four, Dots & Boxes, Reversi, Five in a Row, Checkers, Mancala, Futoshiki, Slitherlink, Hitori, and Bridges. Seven local two-player games support pass-and-play on one device with saved scores. Every single-player game has 30 unlockable levels with saved progress and star ratings. The separate Daily Challenge is an independently generated picture-logic puzzle saved by date; it does not affect regular game progress. Every game has an in-app how-to-play guide. The collection supports English and Arabic, three color themes, optional sound and vibration, offline play, and has no ads or analytics. The web app is in `www/`; it requires no account or network connection for gameplay.

## Test in VS Code

### Run the web app in a browser

1. Open this project folder in VS Code (`File` → `Open Folder…`).
2. Choose `Terminal` → `Run Task…` → `Puzzle Studio: Run web preview` (or run the command below in the integrated terminal).
3. Open `http://localhost:8000` in Chrome or Edge. Stop the server with `Ctrl+C` in the VS Code terminal.

```powershell
python -m http.server 8000 --directory www
```

This runs the web game locally; you can try every puzzle and its settings. If port 8000 is already in use, choose another port in the command and open that port in your browser.

### Run the Android app in an emulator

Install Node.js 22 or later and Android Studio with Android SDK Platform 36. In the VS Code terminal, run these commands from the project root:

```powershell
npm install
npm run android:add
npm run android:sync
npm run android:open
```

Run `npm run android:add` only once. Android Studio opens the native project; start an emulator there and press Run. Use `npm run android:sync` after changing web files so the Android project receives the latest version.
## Android build

This source is ready to be wrapped with Capacitor 8. You need Node.js 22 or later and Android Studio with Android SDK Platform 36 installed.

1. Run `npm install` in this folder.
2. Run `npm run android:add` once to generate the native Android project.
3. Run `npm run android:sync` after web changes.
4. Run `npm run android:open` to open the project in Android Studio.
5. In Android Studio, confirm the generated app targets API 36 or higher, set the final app icon and version, test on real devices, then generate a signed Android App Bundle (AAB) for Play Console.

The `android/` directory is generated locally and is intentionally not included. The web app can also be hosted over HTTPS as a PWA; a hosted PWA by itself is not a Google Play submission package.

## Before Google Play release

- Replace the placeholder package ID if you want a different permanent application ID. The ID cannot be casually changed after publishing.
- Review accessibility, gameplay, photo selection, offline launch, orientation changes, and safe-area layouts on small and large Android devices.
- Prepare final launcher/store graphics, screenshots, store description, support contact, age/content rating, and a public privacy-policy URL.
- Complete Play Console's Data safety and policy forms to match the final binary and all SDKs. This build has no ads, account system, analytics, or network gameplay; selected photos are processed locally. Verify this again after adding anything.
- As of October 14, 2026, new apps and updates must target API 36 or higher. Google can update this rule.
- Google Play requires new personal developer accounts created after November 13, 2023 to complete a closed test with at least 12 testers opted in continuously for 14 days before applying for production access.
- Create and protect your upload key/Play App Signing setup. Never commit private signing keys or credentials.

See `PRIVACY-POLICY.md` for the policy text to review and publish. It is a template until the developer provides an actual contact and hosts it at a publicly accessible URL.

