# 📡 UDP Setup

DashForge receives telemetry data using UDP packets sent by racing games.

---

# Finding Your Device IP

Your game must send telemetry data to the device running DashForge.

Example local IP:

    192.168.1.42

---

# Default Port

DashForge default UDP port:

    8000

You can change the port inside the app settings.

---

# Typical Game Configuration

Most games provide telemetry options similar to:

| Setting | Example |
|---|---|
| UDP Telemetry | Enabled |
| IP Address | 192.168.1.42 |
| Port | 8000 |

---

# Troubleshooting

## No telemetry received

Check:
- game telemetry enabled
- correct IP address
- correct UDP port
- firewall permissions
- same local network

---

## Firewall Issues

macOS may block incoming UDP packets.

Allow DashForge in:

    System Settings → Network → Firewall

---

# Supported Games

Currently supported:
- Forza Horizon 6

Additional games can be added through custom game profiles.
