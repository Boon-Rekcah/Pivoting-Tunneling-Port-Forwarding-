## Scenario

- You have compromised Ubuntu Server
- Ubuntu Server have access to another network that your attacker machine can't access
- We will setup a SSH Dynamic Tunnel and use ProxyChains to use that tunnel for forwarding traffic to unaccessible network

## Required Components

- SSH access on compromised Machine

---

### Configure ProxyChains

Use SSH local port forwarding to expose a locally bound service.

```bash
nano /etc/proxychains4.conf
```
```bash
socks4 127.0.0.1 9050
```
### Enabled Dynamic Port forward

```bash
ssh -D <Port defined in proxychains config in previous step> root@<Target-IP>
```
### Now you should be able to access remote network using ProxyChains

#### Nmap – Network Discovery via ProxyChains
```bash
proxychains nmap -v -sn 192.168.10.0/24
```
#### Metasploit via ProxyChains
```bash
proxychains msfconsole
```
