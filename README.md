# scripts
# Cloudflare Tunnel Manager

A simple script to manage Cloudflare Tunnels from the command line.

## Prerequisites
1. Install `cloudflared`: [Official Install Guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/)
2. Install `jq`: `sudo apt install jq`

## Setup

1. **Environment Variables**
Add to `~/.bashrc` or `~/.zshrc`:
```bash
export CLOUDFLARE_EMAIL="your-email@example.com"
export CLOUDFLARE_API_KEY="your-global-api-key"
export CLOUDFLARE_ZONE_ID="your-zone-id"
export CLOUDFLARE_DOMAIN="yourdomain.com"
```

2. **Install Script**
```bash
# Create scripts directory
mkdir -p ~/scripts

# Download script
curl https://raw.githubusercontent.com/mohilcode/scripts/refs/heads/main/tunnel -o ~/scripts/tunnel

# Make executable
chmod +x ~/scripts/tunnel

# Create symlink
sudo ln -s ~/scripts/tunnel /usr/local/bin/tunnel
```

3. **Authenticate with Cloudflare**
```bash
cloudflared tunnel login
```

## Usage

```bash
# Create tunnel
tunnel create app-name 3000 subdomain

# Create and run as service
tunnel create app-name 3000 subdomain --service

# List tunnels
tunnel list

# Start tunnel
tunnel start app-name

# Delete tunnel
tunnel delete app-name

# View tunnel info
tunnel info app-name

# Stream tunnel logs
tunnel tail app-name
```

## Get Cloudflare Details

1. **API Key**:
   - Cloudflare Dashboard → My Profile → API Tokens → Global API Key

2. **Zone ID**:
   - Cloudflare Dashboard → Your Domain → Overview → Zone ID (right sidebar)

## Notes
- Using `--service` requires sudo access
- Services are created in `/etc/systemd/system/`