# Bitasmbl-Lightweight-Chat-App-No-Auth

Build a web application that allows users to join anonymous chatrooms and exchange messages in real-time using WebSockets. The focus is on fast communication, simple interface, and responsive updates without requiring user registration.

## Tech Stack
- FastAPI
- React
- Socket.IO

## Requirements
- Allow users to join chatrooms without authentication
- Send and receive messages in real-time using WebSockets
- Display messages with timestamps and user identifiers (anonymous)
- Handle multiple chatrooms simultaneously
- Gracefully handle disconnected users and reconnections

## Installation

### Backend
bash
cd backend
python3 -m venv venv
source venv/bin/activate
pip install fastapi uvicorn python-socketio python-engineio

Create a `.env` file in the `backend` folder if needed:
env
# Example
SOCKET_SERVER_HOST=0.0.0.0
SOCKET_SERVER_PORT=8000

Start the backend server:
bash
uvicorn main:app --reload --host ${SOCKET_SERVER_HOST:-0.0.0.0} --port ${SOCKET_SERVER_PORT:-8000}


### Frontend
bash
cd frontend
npm install

Create a `.env` file in the `frontend` folder:
env
REACT_APP_SOCKET_SERVER_URL=http://localhost:8000

Start the React development server:
bash
npm start


## Usage
1. Open your browser and visit `http://localhost:3000`.
2. Enter or select an existing chatroom name.
3. Start sending and receiving messages anonymously in real-time.
4. Open multiple tabs or windows to simulate multiple users in different chatrooms.

## Implementation Steps
1. Initialize the FastAPI project in `backend/main.py`.
2. Install and configure `python-socketio` and integrate with FastAPI via ASGI.
3. Implement WebSocket event handlers: `connect`, `disconnect`, `join_room`, `leave_room`, and `send_message`.
4. Broadcast messages to specific chatrooms, attaching timestamps and anonymous user IDs.
5. Configure CORS in FastAPI to allow the frontend origin.
6. Initialize the React app in the `frontend` folder using Create React App.
7. Install `socket.io-client` and set up environment variables for the socket server URL.
8. Build UI components: chatroom selector, message list (with timestamps and user IDs), and message input.
9. Connect to the Socket.IO server in React, handle incoming and outgoing events, and update the UI in real-time.
10. Implement reconnection logic and display connection status to users.

## API Endpoints
This application leverages Socket.IO events for all real-time communication. No RESTful HTTP endpoints are exposed.