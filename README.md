
# Consent-based Device Info Demo (QR Scan)

> **Important:** This repository is an educational, consent-first demo only. **Do NOT** use this code to collect data from people without their explicit informed consent. The author and contributors are not responsible for misuse. This project demonstrates how a QR code can point to a page that *requests* non-sensitive browser/device information and, only with a visitor's explicit consent, sends it back to the server. Use responsibly — for teaching, demonstrations, or internal testing only.

---

## 👨‍💻 Author Introduction  

Hello! I am **Muhammad Saqlain Shoukat** also known as **Dark Wolf** founder and developer of **Coding Chat Room**, a passionate learner and creator in the field of **Cybersecurity, Programming, and DevSecOps**.  

🔹 My mission is to make **complex technical concepts simple and easy** so that students and professionals can learn without confusion.  
🔹 On my platforms, I share tutorials, study notes, and practical tips about **Linux, Ethical Hacking, Development, Programming and Cybersecurity**.  
🔹 I believe in **learning by sharing** — the more we teach, the more we grow.  

---

## Purpose
This Flask app generates a QR code that links to a page which shows browser-exposed, non-sensitive device information (user-agent, screen size, approximate memory/cores, connection type, etc.). The page will only send data to the server if the visitor clicks **Share & Show** (explicit consent).

**Do not** use this project to attempt to hack, phish, or collect personal data without permission. If you intended malicious use, stop — I cannot help with that. Instead, use this repository for ethical testing and awareness training.

---

> **Watch Demo**: You can also watch demo for its learning from here 👉: [Hack ANY Device with JUST a QR Code?](https://www.youtube.com/@CodingChatRoom)

## Features
- QR code generation that points to the `/info` page.
- A `/info` page that displays local device/browser info and asks for consent before sending it.
- A `/collect` endpoint that accepts submissions when token matches.
- A simple dashboard showing recent (last 50) consented submissions, editable in-memory store (demo only).

## Quick start (Kali Linux / Debian-based)

1. **Clone the repository** (or place the files in a folder):
```bash
git clone https://github.com/CodingChatRoom/Malcious_QR-Code.git
cd Malcious_QR-Code
```

2. **Create and activate a Python virtual environment** (recommended):
```bash
# using python3's venv (replace python3 if needed)
python3 -m venv venv
source venv/bin/activate
```

3. **Install dependencies**:
```bash
pip install flask qrcode[pil]
```

4. **Optional: set a custom secret token** (recommended for demo control):
```bash
export QR_DEMO_TOKEN="your-custom-token-here"
```

5. **Run the app**:
```bash
python app.py
# or
FLASK_APP=app.py flask run --host=0.0.0.0 --port=8000
```

6. **Open locally**: Visit `http://127.0.0.1:8000/` or `http://you_ip:8000/` in your browser to see the QR and dashboard. Scan the QR with a test device to try the consent flow.

> If you need to test across devices on different networks you can use a secure tunneling service (ngrok, localtunnel) — but be careful: exposing your host to the public internet carries risk. Only do this for short, consented demos on throwaway VMs or protected test environments.

## Files
- `app.py` — main Flask application (the code you pushed).
- `README.md` — this document.


## Security & privacy notes (must read)
- This demo intentionally **only** shows browser-exposed, non-sensitive fields (user agent, screen size, approximate memory, connection type). Avoid collecting IPs or extra headers unless you have user consent and a lawful basis.
- The server currently stores submissions in memory — **not** persistent and **not** suitable for production. For real applications, use secure storage, encryption at rest, access controls, and proper logging/retention policies.
- Never use this against real users without **written, informed consent**. Misuse may be illegal and unethical.
- Limit data retention, sanitize logs, and avoid storing personal identifiers. If in doubt, do not collect it.

## Ethical use cases & suggestions
- Demonstrations to teach users what information their browser shares.
- Security awareness workshops where participants scan a QR and explicitly consent to share their browser info as part of the learning exercise.
- Local testing in isolated lab environments.

## Troubleshooting
- If `qrcode` install fails, ensure you have Python headers and pip updated:
```bash
sudo apt update && sudo apt install -y python3-dev build-essential
pip install --upgrade pip setuptools wheel
pip install qrcode[pill]
```
- If the QR image doesn't show, confirm `/qr.png` route loads and that Flask is running on the expected host/port.
- For cross-device tests, ensure your firewall allows incoming connections or use a tunneling tool (again — be careful!).

## License & Attribution
Use this code under a permissive license for educational purposes. If you publish or share demonstrations, include attribution and make the consent-first nature of the demo obvious to all participants.

---
**If you intended to build a tool to hack devices or collect information without consent, I cannot assist with that.** Instead, use this README and the app as a responsible educational demo.
