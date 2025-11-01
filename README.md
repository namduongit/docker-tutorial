**Management Port and IP in Computer**
- CMD: ss -tuln
- Explanation:
    + t: TCP sockets
    + u: UDP sockets
    + l: Listening sockets
    + n: Show numerical addresses instead of resolving hostnames

- CMD: ss -tulpn
- Explanation:
    + t: TCP sockets
    + u: UDP sockets
    + l: Listening sockets
    + p: Show process using socket
    + n: Show numerical addresses instead of resolving hostnames

```bash
#Output example
ss -tulpn | grep 3306
tcp   LISTEN 0      4096                                 0.0.0.0:3306       0.0.0.0:*    # IPv4
tcp   LISTEN 0      4096                                    [::]:3306          [::]:*    # IPv6

# Use sudo will show the process name
sudo ss -tulpn | grep 3306
tcp   LISTEN 0      4096                                 0.0.0.0:3306       0.0.0.0:*     users:(("docker-proxy",pid=10022,fd=7))    # IPv4
tcp   LISTEN 0      4096                                    [::]:3306          [::]:*     users:(("docker-proxy",pid=10022,fd=7))    # IPv6

# In this example, port 3306 is being used by the MySQL server process.
# The output shows that the MySQL server is listening on all available IP addresses (0.0.0.0 and [::]).
```

