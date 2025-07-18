# 🔌 WebSocket Bridge for Webhook Broadcast

A simple Go server that bridges incoming HTTP POST (webhook) requests to connected WebSocket clients in real-time.

## 🚀 Features

* Accepts WebSocket connections at `/ws`
* Accepts incoming webhook POST requests at `/webhook`
* Forwards the webhook body to all connected WebSocket clients
* Thread-safe client management
* Built with `net/http` and `gorilla/websocket`

## 📦 Installation

```bash
git clone https://github.com/your-username/websocket-bridge.git
cd websocket-bridge
go run main.go
```

The server will start on:
`http://localhost:8080`

## 📡 Endpoints

### `/ws` – WebSocket Endpoint

Connect your frontend client to this endpoint to receive real-time messages from the server.

**Example (JavaScript):**

```js
const socket = new WebSocket("ws://localhost:8080/ws");

socket.onmessage = (event) => {
  console.log("New message from server:", event.data);
};
```

### `/webhook` – Webhook POST Receiver

Send a POST request to this endpoint. The body of the request will be broadcasted to all connected WebSocket clients.

**Example (cURL):**

```bash
curl -X POST http://localhost:8080/webhook \
  -H "Content-Type: application/json" \
  -d '{"message": "Hello WebSocket Clients!"}'
```

## 🧐 Use Cases

* Bridging WhatsApp webhook events (e.g., from WhatsMeow) to frontend apps
* Real-time dashboards
* Logging tools
* Bot development tools

## ⚠️ CORS / Origin Policy

This server currently allows all origins by default:

```go
CheckOrigin: func(r *http.Request) bool {
  return true
}
```

For production use, it's recommended to restrict allowed origins.

## 📁 File Structure

```
.
├── main.go         # Main server code
├── README.md       # This documentation
```

## 📃 License

MIT – free to use, modify, and distribute.

---

Made with 💡 and Go.
