🟩 MASTER PROCEDURE – FULL REMOTE ACCESS SETUP
🟦 STEP 1 — Install Zerotier on Raspberry Pi 5

Run these commands on Pi:
```
curl -s https://install.zerotier.com | sudo bash
sudo zerotier-cli join <NETWORK_ID>
```

Check if connected:
```
sudo zerotier-cli listnetworks
```

You should see status:
OK PRIVATE <NETWORK_ID>

🟦 STEP 2 — Install Zerotier on Office PC (Ubuntu)
```
curl -s https://install.zerotier.com | sudo bash
sudo zerotier-cli join <NETWORK_ID>
```

Check:
```
sudo zerotier-cli listnetworks
```
🟦 STEP 3 — Authorize Devices in Zerotier Dashboard

Go to:
```
👉 https://my.zerotier.com/network/<NETWORK_ID>
```
For each device:

✔ Tick Authorize
✔ It will get an IP like: 192.168.xxx.xxx

This is your VPN IP.

🟦 STEP 4 — SSH Into Raspberry Pi (From Office PC)

Use Zerotier IP:
```
ssh thirdumpire-v1@<Pi_Zerotier_IP>
```

Example:
```
ssh thirdumpire-v1@192.168.193.137
```

If first time:

yes


Enter password → you are inside the Pi.

🟩 STEP 5 — Enable WayVNC on Raspberry Pi 5 (Wayland)

Pi 5 uses Wayland, so RealVNC is not used.

1️⃣ Install WayVNC (already present in Pi OS)

Ensure it's installed:
```
sudo apt install wayvnc -y
```

Enable + start:
```
sudo systemctl enable wayvnc
sudo systemctl start wayvnc
```

Check status:
```
systemctl status wayvnc
```
🟩 STEP 6 — Configure WayVNC Password

Create/edit config:
```
mkdir -p ~/.config/wayvnc
nano ~/.config/wayvnc/config
```

Paste:
```
address=0.0.0.0
enable_auth=true
password=scl
```

Save → restart:
```
sudo systemctl restart wayvnc
```
🟩 STEP 7 — Install VNC Viewer on Office PC

Option A — TigerVNC:
```
sudo apt install tigervnc-viewer -y
```

Connect:
```
vncviewer <Pi_Zerotier_IP>
```

Password: sclabs
Username: leave blank

Open GUI → Add new connection:

🟦 STEP 8 — Full Remote Access Achieved

✔ SSH working
✔ VNC GUI working
✔ Secure via Zerotier
✔ Connect from anywhere in the world
