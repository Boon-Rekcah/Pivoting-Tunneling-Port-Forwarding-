## Scenario

- You have compromised an Ubuntu server.
- The Ubuntu server has port **3306 (MySQL)** open, but it is **bound locally**.
- The service **cannot be accessed directly** from the attacker machine.

## Goal

Forward port **3306** from the compromised Ubuntu server to the attacker machine so the service can be accessed remotely.

## Required Components

- SSH access to the compromised machine

---

## Single Port Forward

### From the Attacker Machine

Use SSH local port forwarding to expose a locally bound service.

```bash
ssh -L <Attacker_Port>:localhost:<Target_Port> root@<Target IP>
```
## Multiple Port Forward

```bash
ssh -L 1234:localhost:3306 -L 8080:localhost:80 root@<Target IP>
```
