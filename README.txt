TIDAL FRONTIER — MEGA UPDATE

Upload index.html, server.js, package.json and .gitignore to your existing GitHub repository.
Deploy as a Render WEB SERVICE (Node.js), not GitHub Pages static hosting.
Build command: npm install
Start command: npm start

FEATURES: Leaderboards, Kraken boss battle, Golden/Rainbow/Shadow fish, daily rewards, money trading, bounties, arena wagering, 5 extra boats, full cooler inventory, rotating ocean weather, quests, upgradeable player bases. Open MEGA UPDATE in-game.

LOGIN FIX: usernames are trimmed and case-insensitive, passwords can be 3+ characters, and sessions are persisted to a JSON file. New errors distinguish missing accounts from incorrect passwords. Login test passed locally.

IMPORTANT: Render's ephemeral filesystem is NOT permanent. Set ACCOUNT_DATA_FILE=/var/data/accounts.json, SESSION_DATA_FILE=/var/data/sessions.json, GAME_DATA_FILE=/var/data/world.json and attach a persistent disk mounted at /var/data. If your Render plan does not support persistent disks, you must use a database or a persistent host instead. Previously deleted accounts cannot be recovered without a backup. Don't create new accounts until persistent storage is configured if you need progress to survive redeploys.

Trade system currently supports money gifts held in escrow, not fish/rod swaps. Arena is a wagered random showdown, not a separate movement map. Boss is a cooperative server health bar. Bases are upgradeable levels, not yet editable 3D houses. Weather changes water appearance, not movement physics. Client-reported money remains susceptible to cheating; a fully secure economy requires server-authoritative progression.

Existing chat, codes, fish index, islands, PvP 20% death penalty, and Buddy Big Stick are retained. Test live multiplayer before publishing broadly.

CHROMEBOOK PERFORMANCE UPDATE: low graphics by default; quality button; culling, frame-time movement, non-overlapping multiplayer sync.

PERFORMANCE PATCH (November 5): Low graphics limits rendering to ~30 FPS, draws fewer water waves and island decorations, and reduces multiplayer polling to ~1.2 updates/sec. Position is saved periodically rather than rewriting progress every five seconds. Saves are deduplicated, and temporary connection errors no longer erase the stored login token.

NOTE: A Render persistent disk or external database is still required to preserve accounts across deployments. A browser-only code update cannot make ephemeral server storage permanent. Server/client multiplayer and account persistence should be tested on the actual deployed host.

3D PROTOTYPE + CLANS (NEW)
- Start server as before (npm start), then visit /3d.html for the separate 3D prototype.
- The original 2D game stays at / and remains unchanged.
- 3D prototype requires internet to load Three.js from jsDelivr.
- This is an early playable 3D scene, not photorealistic and not yet a full 3D port of all fishing systems.
- 3D fishing catches are demo-only and do not save to the original fish inventory.
- The 3D scene does not yet sync other players or boats; original multiplayer remains in 2D.
- Clan API: /clans, /clans/me, /clans/action. Create, join, leave; 30-member cap.
- Clan membership is tied to original game accounts. Log in at / first.
- Clan data persists in clans.json. For Render persistence, set CLAN_DATA_FILE to a persistent disk path, just as with account storage.
- Performance mode toggles resolution and shadows for Chromebook compatibility.
