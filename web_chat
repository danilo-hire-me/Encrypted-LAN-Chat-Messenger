from flask import Flask, render_template
from flask_socketio import SocketIO, send
from Crypto.Cipher import AES
from Crypto.Util.Padding import pad, unpad
import base64

app = Flask(__name__)
app.config["SECRET"] = "secrfet!123"
socketio = SocketIO(app, cors_allowed_origins="*")


SECRET_KEY = b'my_secret_key_16b'  # Must be 16, 24, or 32 bytes long

def encrypt_message(message):
    cipher = AES.new(SECRET_KEY, AES.MODE_CBC)
    ct_bytes = cipher.encrypt(pad(message.encode('utf-8'), AES.block_size))
    iv = base64.b64encode(cipher.iv).decode('utf-8')
    ct = base64.b64encode(ct_bytes).decode('utf-8')
    return iv + ct

def decrypt_message(ciphertext):
    iv = base64.b64decode(ciphertext[:24])
    ct = base64.b64decode(ciphertext[24:])
    cipher = AES.new(SECRET_KEY, AES.MODE_CBC, iv)
    pt = unpad(cipher.decrypt(ct), AES.block_size)
    return pt.decode('utf-8')

@socketio.on('message')
def handle_message(ciphertext):
    message = decrypt_message(ciphertext)
    print("Received message: " + message)
    if message != "User connected!":
        send(encrypt_message(message), broadcast=True)

@app.route('/')
def index():
    return render_template("index.html")

if __name__ == "__main__":
    socketio.run(app, host="192.168.1.12")