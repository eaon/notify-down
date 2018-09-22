# Simple Signal downtime notification for TLS, HTTP, and machines that respond to ICMP packets

Depends on [signal-cli](https://github.com/AsamK/signal-cli), curl, ping,
grep, coreutils, bash and OpenSSL. systemd is optional, you can also run it
via cron if you prefer that.

Expects two files: `~/.config/notify-down/conf`:

```sh
NOTIFY_DOWN_FROM="+15555892342"
NOTIFY_DOWN_TO="+15550931337"
```

The first number of which has to be an account already set up with signal-cli,
the second a number that is registered on the network.

`~/.config/notify-down/services`:

```
Example HTTP Service,example.org,80,http
Example TLS Service,example.net,443,tls
Example STARTTLS Service,eggs.gnu.org,25,starttls smtp
Example PING Service,example.com,,ping
```

FYI, TLS service checks also fail if there's a "verify error" found in the
certificate chain.
