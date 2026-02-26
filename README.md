# QuoRoom - Live Q&A Platform

A real-time Q&A platform where hosts create sessions and attendees join via a code.

## Quick Start

### 1. Install Dependencies

```bash
cd quoroom
npm install
```

### 2. Start the Server

```bash
npm start
```

You'll see:
```
╔════════════════════════════════════════════════════════════╗
║                                                            ║
║   🎤 QuoRoom Server Running!                               ║
║                                                            ║
║   Host Console:     http://localhost:3000/host             ║
║   Attendee App:     http://localhost:3000/                 ║
║                                                            ║
╚════════════════════════════════════════════════════════════╝
```

### 3. Use the Platform

**On your computer (Host):**
1. Open `http://localhost:3000/host`
2. Click "Create New Session"
3. You'll get a 6-character code (e.g., `XK7M2P`)

**On your phone (Attendee):**
1. Find your computer's local IP address:
   - Mac: `ipconfig getifaddr en0`
   - Windows: `ipconfig` → look for IPv4 Address
   - Linux: `hostname -I`
2. On your phone, open `http://YOUR_IP:3000`
   - Example: `http://192.168.1.100:3000`
3. Enter your name and the session code
4. Tap "I Have a Question" to join the queue!

## How It Works

```
┌─────────────────┐         ┌─────────────────┐
│   Host (PC)     │◄───────►│   Server        │◄───────►│   Attendee      │
│   /host         │ Socket  │   Node.js       │ Socket  │   (Phone)       │
│                 │         │   + Socket.io   │         │   /             │
└─────────────────┘         └─────────────────┘         └─────────────────┘
```

- **Real-time sync** via WebSockets (Socket.io)
- **Session persists** as long as the server runs
- **Multiple attendees** can join the same session
- **Queue management** with fair FIFO ordering

## Features

### Host Console
- Create sessions with unique 6-character codes
- See attendees join in real-time
- View queue with names, positions, and notes
- Grant permission to next speaker
- Mark speakers as complete
- Skip speakers (move to end of queue)
- Remove people from queue
- Fullscreen code display for projection

### Attendee App
- Join via code on any device
- Raise hand to join queue
- See your position in real-time
- Get notified when it's your turn
- Add private notes for your question
- Speaking timer
- Leave queue anytime

## Project Structure

```
quoroom/
├── server/
│   └── index.js      # Express + Socket.io server
├── public/
│   ├── host.html     # Host console (desktop)
│   └── attendee.html # Attendee app (mobile)
├── package.json
└── README.md
```

## Configuration

Change the port by setting the `PORT` environment variable:

```bash
PORT=8080 npm start
```

## For Production

For a production deployment, you would:

1. **Add a database** (Redis/PostgreSQL) for session persistence
2. **Add authentication** for hosts
3. **Add HTTPS** with SSL certificates
4. **Deploy to a cloud provider** (Heroku, Railway, Fly.io, etc.)
5. **Add a real QR code** using a library like `qrcode`

## Tech Stack

- **Backend:** Node.js, Express, Socket.io
- **Frontend:** Vanilla HTML/CSS/JS (no framework needed)
- **Communication:** WebSockets for real-time updates

## License

MIT
