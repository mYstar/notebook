# Networking

## DNS problems (17.10)

After using Cisco VPN:
* internet connection
* `ping 8.8.8.8` works
* but no DNS resolve: `dig www.google.de` fails

**Solution**:
1. edit: `/etc/resolv.conf`
2. remove cheeky `nameserver 127.0.0.1` (or similar) lines
3. insert:

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

4. `ping www.google.de` works
