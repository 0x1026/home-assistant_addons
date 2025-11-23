# Home Assistant Add-on: Cloudflared

## How to use

This add-on allows you to run Cloudflare Tunnel (cloudflared) on your Home Assistant host.

### Configuration

Before starting the add-on, you need to create a tunnel in the Cloudflare dashboard:

1. Go to [Cloudflare Zero Trust dashboard](https://one.dash.cloudflare.com/)
2. Navigate to Networks > Tunnels
3. Create a new tunnel
4. Copy the tunnel token

Then, configure the add-on with your tunnel token:

```yaml
tunnel_token: "your-tunnel-token-here"
```

### Starting the tunnel

Once configured, start the add-on. The tunnel will connect to Cloudflare and you can configure your routes in the Cloudflare dashboard.

The add-on runs with host network mode to allow proper connectivity to services running on your Home Assistant host.
