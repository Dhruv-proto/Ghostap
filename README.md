# 👵️‍♂️ Ghostap — Hunting Malicious Telegram Bots

Ghostap is a security research tool designed to **take over and monitor malicious or insecurely configured Telegram bots**.
It works by leveraging exposed **bot tokens** and **chat IDs** to silently forward all incoming messages from the target bot to a Telegram account controlled by the user.

> ⚠️ **Disclaimer:**
> Ghostap is intended strictly for **educational**, **research**, and **authorized security testing** purposes only.
> Unauthorized access to Telegram bots or third-party systems is illegal. The author is not responsible for any misuse of this tool.

---

## 🧠 How It Works

Many malicious or poorly implemented Telegram bots expose their **bot tokens** and **chat IDs** in public repositories or insecure websites. Ghostap exploits this weakness to impersonate the bot and reroute all its communication.

1. **Token & Chat ID Collection**

   * The user provides the target bot’s token and chat ID (often leaked through phishing sites or insecure code).

2. **Bot Validation**

   * Ghostap uses Telegram's `getMe` API method to validate if the bot token is valid and accessible.

3. **Message Enumeration**

   * It fetches the latest message ID using the `getUpdates` method to determine where to start forwarding.

4. **Message Forwarding**

   * Using `forwardMessage`, Ghostap forwards each message from the malicious bot’s chat to **your own Telegram account**, which you configure in a `.env` file.

Because Telegram does not alert bot owners when their messages are forwarded this way, the process is typically silent — highlighting how dangerous exposed tokens can be.

---

## 🧰 Requirements

* Python 3.8+
* A Telegram account
* Telegram API credentials (`api_id`, `api_hash`)
* A `.env` file with your details

---

## ⚙️ Setup Instructions

1. **Clone the Repository**

   ```bash
   git clone https://github.com/Dhruv-proto/ghostap.git
   cd ghostap
   ```

2. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

3. **Create a `.env` File**
   In the root of the project, create a `.env` file with the following content:

   ```env
   API_ID=your_telegram_api_id
   API_HASH=your_telegram_api_hash
   PHONE_NUMBER=+911234567890
   ```

4. **Run the Tool**

   ```bash
   python ghostap.py
   ```

5. **Provide Target Credentials**

   * When prompted, enter the **Bot Token** and **Chat ID** of the insecure bot you want to monitor.
   * Ghostap will validate the bot and begin forwarding its messages to your Telegram account.

---

## 🧪 Example Usage

```bash
$ python ghostap.py
Enter Bot Token: 123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11
Enter Chat ID: 987654321
[+] Bot validated successfully!
[+] Latest message ID: 250
[+] Forwarding messages...
[✔] Message ID 250 forwarded
[✔] Message ID 249 forwarded
...
[✓] All messages have been successfully forwarded to your chat.
```

---

## 📌 Features

* ✅ Validate Telegram bots via `getMe`
* 📩 Fetch and forward messages via `getUpdates` + `forwardMessage`
* 🌐 Works cross-platform (Windows, macOS, Linux)
* 🧠 Built with Python, using Telegram Bot API
* 🧰 Lightweight and easy to set up

---

## 🚀 Future Enhancements

* 🔍 Automated scanning for leaked bot tokens in public repositories
* 📡 Multi-bot monitoring support
* 📝 Database logging for forensic analysis
* ⚠️ Responsible disclosure module to notify bot owners

---

## 📜 License

This project is licensed under the **MIT License**.
See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

Developed as part of a security research project at **National Forensic Sciences University**.
Ghostap is a proof-of-concept to **raise awareness among developers and security professionals** about the dangers of leaked bot credentials.

---


