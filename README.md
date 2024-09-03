LAN Messenger Chat with End-to-End Encryption
This project is a simple LAN-based messenger application that allows users to send and receive messages within the same network. The messages are encrypted before being sent and decrypted upon receiving, ensuring secure communication.

Features
Real-Time Messaging: Communicate instantly over a LAN.
End-to-End Encryption: Messages are encrypted before being sent and decrypted upon receiving to ensure privacy.
User-Friendly Interface: Simple and clean UI for easy use.
Technologies Used
Flask: A lightweight WSGI web application framework in Python.
Flask-SocketIO: Enables real-time communication between the server and clients.
Socket.IO: Handles real-time, bidirectional communication between web clients and servers.
jQuery: Simplifies HTML DOM tree traversal and manipulation.
CryptoJS: A JavaScript library used for encryption and decryption of messages on the client side.
PyCryptodome: A Python library used for encryption and decryption on the server side.
How It Works
Encryption:

The message is encrypted using AES (Advanced Encryption Standard) before being sent to the server.
The encryption is handled by CryptoJS on the client side.
Decryption:

Upon receiving the message, it is decrypted using the same key.
Decryption is handled by CryptoJS on the client side for displaying and by PyCryptodome on the server side for processing.
Real-Time Communication:

Flask-SocketIO and Socket.IO manage the real-time communication between clients and the server.
Setup Instructions
Prerequisites
Python 3.x
Flask
Flask-SocketIO
PyCryptodome

Installation

1.Clone the repository:

git clone https://github.com/yourusername/lan-messenger-chat.git
cd lan-messenger-chat

2.Install the required Python packages:

pip install Flask Flask-SocketIO pycryptodome

3.Run the Flask server:

python app.py

4.Access the application:

Open a web browser and go to http://192.168.1.12:5000 or replace with your server's IP address.

Usage

Enter your username in the input field.
Type your message in the message input field.
Click the "Send" button to send your message.
The message will be encrypted, sent to the server, and broadcast to all connected clients.

File Structure

├── app.py             # The Flask application and Socket.IO server
├── templates
│   └── index.html     # The main HTML file with front-end code
└── README.md          # Project documentation

Security Considerations
Encryption Key: The encryption key is hardcoded for simplicity. In a production environment, it is crucial to securely manage keys and consider key rotation.
Local Network: This application is designed for use within a secure local network. For deployment over the internet, additional security measures, such as SSL/TLS, should be implemented.
