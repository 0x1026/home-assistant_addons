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

#### About Host Network Mode

**Why is host network mode necessary?**

Host network mode is required so that the add-on can access Home Assistant and other services running on the host system. This allows the tunnel to expose these services to Cloudflare as intended.

**Security implications**

When running in host network mode, the add-on container has full access to the host's network stack. This means it can see and interact with all network traffic on the host, which increases the potential attack surface. If the add-on or its dependencies are compromised, an attacker could potentially access other services running on the host.

**Firewall and security considerations**

- Ensure that your Home Assistant host's firewall is properly configured to restrict access to sensitive services
- Only expose the necessary ports and services through the tunnel
- Regularly update the add-on to receive security patches
- Review the permissions granted to the add-on
- Monitor your Cloudflare dashboard for unexpected tunnel activity
