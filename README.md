# ROTK

![Realm of the Kings](src/web/wwwroot/public/assets/img/rooms/ROTK.png)

Realm of the Kings, a text adventure with pixel-art scenes. In the province of Kaseon a new queen is about to be
crowned in the capital, Wolburg, and you play through the story by picking actions: look around, talk to characters,
pick things up, use them and travel on. 21 rooms, 20 characters and close to 40 items, from maps and torches to the two
halves of a medallion. Speedrun mode adds a timer. A Software Engineering project from block 3 at the HvA (2024), by
Borys, Jay, Joas, Mathijs and Salim.

## Stack

| | |
|---|---|
| Frontend | Lit web components, TypeScript, Vite |
| Backend | Express API in TypeScript, run with `tsx` and bundled with esbuild |
| Shared | Types used by both sides in `src/shared` |
| Docs | MkDocs with the Material theme |

## Getting started

```bash
npm install
npm run dev     # web on http://localhost:3000, API on the port in src/api/.env
```

```bash
npm run build     # -> dist/web and dist/api
npm run preview   # build, then serve both
```

The web app finds the API through `VITE_API_URL` in `src/web/.env`. The original project also pulled in packages from
the HBO-ICT Cloud registry, which only works with a student account.

## How the game works

The API holds the game: every room, character and item is a class with its own text, pictures and actions. The
frontend sends the action you clicked, the API runs it against your session and answers with the next text, images
and the actions you can take now.

| Folder | |
|---|---|
| `src/api/src/rooms/` | The 21 rooms, from the intro and Wolburg's gate to the throne room and Smaug's chamber |
| `src/api/src/characters/` | Everyone you can talk to or fight |
| `src/api/src/items/` | Maps, torches, weapons, armour, potions and quest items |
| `src/api/src/actions/` | Navigate, pick up, use, attack and check inventory |
| `src/api/src/base/` | The engine: game objects, action results and the player session |

## Project structure

| Path | |
|---|---|
| `src/web/src/components/` | `StartScreen` (load game, how to play, speedrun mode) and `GameCanvas` |
| `src/web/src/services/` | Talking to the API, and routing |
| `src/web/wwwroot/` | The page, styles, fonts and the room artwork |
| `src/api/src/` | Express app, routes and the game itself |
| `src/shared/types.ts` | Request and response types |
| `docs/` | Team documents, retrospectives and personal documentation |
