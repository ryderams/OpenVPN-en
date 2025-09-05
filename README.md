# OpenVPN — Quick installation and setup

## 🚀 1. VPS with bonus

You need a VPS to run OpenVPN. We recommend using **aeza** and getting a top-up bonus:

👉 [aeza](https://aeza.net/?ref=537145)

When you top up your balance, you receive a 15% bonus on the top-up amount. The bonus is valid for 24 hours after the top-up.

---

## ⚡ 2. Install OpenVPN

Download and run the automated installation script:

```bash
wget -O openvpn.sh https://get.vpnsetup.net/ovpn
sudo bash openvpn.sh --auto
```

### 🔑 Script modes
 - `--auto` — fully automated install with default settings.

> Note: in `--auto` mode the script automatically creates the first client — its name is printed at the end of the installation. To export the client configuration directly, run:

```bash
sudo bash openvpn.sh --exportclient <name> > <name>.ovpn
```

The generated `.ovpn` file may also be left in the `root` home folder (`/root`). If so, find and copy it with:

```bash
sudo ls /root/*.ovpn     # show generated .ovpn files
sudo cp /root/<name>.ovpn ./  # copy the file to the current directory
sudo chown $(whoami):$(whoami) ./<name>.ovpn  # (optional) change owner
```

---

## 🛠 3. Useful script commands

After installation you can use the script to manage the server:

```bash
sudo bash openvpn.sh --help
```

Available flags:

- `--addclient [name]` — add a new client.
- `--exportclient [name]` — export a client configuration to `.ovpn`.
- `--listclients` — list all clients.
- `--revokeclient [name]` — revoke/remove a client.
- `--uninstall` — remove OpenVPN and all settings.
- `--yes` / `-y` — answer "yes" to all prompts.
- `--listenaddr [IP]` — set the IP address the server listens on.
- `--serveraddr [DNS/IP]` — set the server domain or IP.
- `--proto [UDP/TCP]` — choose protocol (UDP by default).
- `--port [number]` — server port (1194 by default).

---

## 👤 4. Examples

### Add a client
```bash
sudo bash openvpn.sh --addclient user1
```

### Export a client config
```bash
sudo bash openvpn.sh --exportclient user1 > user1.ovpn
```

### List clients
```bash
sudo bash openvpn.sh --listclients
```

### Revoke a client
```bash
sudo bash openvpn.sh --revokeclient user1
```

### Uninstall OpenVPN completely
```bash
sudo bash openvpn.sh --uninstall
```

---

## ❓ 5. FAQ

| Question | Solution |
|---------|---------|
| Client cannot connect | Check that UDP/1194 is open in the firewall |
| TLS Error: TLS key negotiation failed | Check server time and date synchronization |
| No internet through VPN | Add NAT/forwarding rules (iptables/ufw) |
| Want TCP instead of UDP | Install with `--proto tcp` |

---

## 📌 6. Useful links
- [OpenVPN documentation](https://openvpn.net/community-resources/)
- [Installer script repository](https://github.com/hwdsl2/openvpn-install)
- [aeza (top-up bonus 15% for 24 hours)](https://aeza.net/?ref=537145)

---

💡 You now have a quick way to deploy OpenVPN on a VPS in a few minutes.
