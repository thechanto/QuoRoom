# QuoRoom - Live Q&A Platform

A real-time Q&A platform where hosts create sessions and attendees join via a code.

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
## License

MIT
