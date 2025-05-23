# DarkChat

A privacy-focused, encrypted messaging web app designed to run as a hidden service on the Tor network. All messages are encrypted client-side using AES and exchanged asynchronously via a session key.

---

## 🚀 Features

- 💬 Asynchronous secure messaging
- 🔐 Client-side AES encryption/decryption
- 🧾 Session-based communication
- 🌐 Onion service-ready
- 🖥️ No user login or accounts

---

## 📁 Project Structure

secure-messaging/
├── public/
│   ├── index.html              # Landing page  
│   ├── session_creator.html    # Generate new session  
│   ├── session_joiner.html     # Join an existing session  
│   ├── chat.html               # Encrypted chat interface  
│   ├── matrix.js               # Encryption & UI logic  
│   └── style.css               # Minimal modern dark theme  
├── server.js                   # Express server with SQLite backend  
├── messages.db                 # SQLite database (auto-generated)  
├── .env                        # Tor hidden service config (optional)  
└── README.md                   # You are here

---

## 🧪 Local Setup Instructions

### 1. 🔧 Prerequisites

Ensure you have:

- Node.js (v14 or newer)
- npm (comes with Node)
- Tor Browser or Tor daemon installed if hosting as onion

### 2. 📦 Install dependencies

npm install express sqlite3 cors

### 3.our app will now be running at:
      http://localhost:3000
4. 🌐 Navigate through pages

    index.html → intro & links

    session_creator.html → create a session key

    session_joiner.html → join an existing session

    chat.html?session=KEY → chat interface (auto-loaded via key)▶️ Start the server
 
    node server.js

5.Deploying on Tor (Hidden Service)

    Requires Tor installed and running on Linux

1. Edit torrc file

sudo nano /etc/tor/torrc

2. Add Hidden Service config

HiddenServiceDir /var/lib/tor/secure-messaging/
HiddenServicePort 80 127.0.0.1:3000

3. Restart Tor

sudo service tor restart

4. Get your .onion address

sudo cat /var/lib/tor/secure-messaging/hostname

Use that .onion link in the Tor Browser to access your hidden site.

🔐 Encryption

    AES-GCM used for encrypting messages

    No private keys are stored or logged

    Only those with the session key can decrypt messages

🧼 Notes

    Messages are stored encrypted in SQLite and deleted after session end

    No login, tracking, or cookies

    Built for privacy-first secure communication
