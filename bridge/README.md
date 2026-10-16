# Bridge deployment

The browser cannot open Ragnarok's TCP ports directly. For real connections, deploy an upstream-compatible WebSocket proxy on a VPS or alongside your game server. See https://github.com/MrAntares/roBrowserLegacy-wsProxy .

Example (only for a server YOU control, with TLS termination at your reverse proxy):

```bash
npm install -g wsproxy
wsproxy -p 5999 -a 127.0.0.1:6900,127.0.0.1:6121,127.0.0.1:5121
```

Publish `wss://bridge.example.net/` via a TLS-enabled reverse proxy that forwards WebSocket upgrades to local port 5999. Only allow intended game server addresses. This sample does not configure TLS, DNS, firewall rules or an asset service. For non-local servers, explicitly list the authorized server's login, char and map host:port pairs; ensure returned addresses are reachable/redirected as required. Do not use a publicly accessible unrestricted proxy.
