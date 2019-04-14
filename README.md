# Simple downtime notifications for TLS, HTTP, and machines that respond to ICMP packets

Depends on [signal-cli](https://github.com/AsamK/signal-cli) if you want
Signal notifications. curl, ping, grep, coreutils, nc, Bash and OpenSSL are
required for everything else to work. systemd is optional, you can also run
`notify-down` via cron if you prefer that.

Expects two files: `~/.config/notify-down/conf`:

```sh
NOTIFY_DOWN_FROM="+15555892342" # Signal only
NOTIFY_DOWN_TO="+15550931337" # Signal only
NOTIFY_DOWN_SLACK="https://hooks.slack.com/services/SOMETHING/ORxOTHER/HEXADECIMALKEY" # Slack only
NOTIFY_DOWN_PREFIX="Something added in front of the notification text … "
```

The `NOTIFY_DOWN_FROM` number has to be already set up with signal-cli for the
user that runs the script, the `NOTIFY_DOWN_TO` can only be a number that is
registered on the network.

`NOTIFY_DOWN_PREFIX` is probably only useful to `@someone` on Slack.

`~/.config/notify-down/services` is a comma separated list:

```
Example HTTP Service,example.org,80,http
Example TLS Service,example.net,443,tls
Example STARTTLS Service,eggs.gnu.org,25,starttls smtp
Example PING Service IPv4,example.com,,ping4
Example PING Service IPv6,example.com,,ping6
Example PING Service Protocol Agnostic,example.com,,ping
Example TCP Service,towel.blinkenlights.nl,23,tcp
```

FYI, TLS service checks also fail if there's a "verify error" found in the
certificate chain.
