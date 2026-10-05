# ws_test

A small real-time chat / notification demo: a [Next.js](https://nextjs.org) frontend talking to a standalone [`ws`](https://github.com/websockets/ws) WebSocket server.

## How it works

- **`server.js`** – plain Node WebSocket server on `ws://localhost:8080`. It greets each new client with a welcome message and broadcasts every received message to all connected clients (including the sender).
- **`app/components/NotificationCenter.js`** – client component that opens a WebSocket connection to the server, lists incoming messages, and provides an input + **Send** button.
- **`app/page.tsx`** – home page rendering `NotificationCenter`.

## Getting Started

Install dependencies. The WebSocket server needs the `ws` package, which is not listed in `package.json`, so install it too:

```bash
npm install
npm install ws
```

Run the two processes in separate terminals:

```bash
# 1. WebSocket server (port 8080)
node server.js

# 2. Next.js dev server (port 3000)
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in two or more browser tabs, type a message and press **Send**. It appears in every open tab.

## Scripts

| Command         | Description                  |
| --------------- | ---------------------------- |
| `npm run dev`   | Start the Next.js dev server |
| `npm run build` | Build for production         |
| `npm start`     | Run the production build     |
| `npm run lint`  | Lint with ESLint             |

## Stack

Next.js 16 (App Router), React 19, TypeScript, Tailwind CSS 4, `ws`.

## Notes

- The WebSocket URL (`ws://localhost:8080`) is hard-coded in `NotificationCenter.js`; change it there when deploying.
- Messages are not persisted – only clients connected at the time receive a broadcast.
- This Next.js version has breaking changes from older releases; see `node_modules/next/dist/docs/` and `AGENTS.md` before changing app code.
