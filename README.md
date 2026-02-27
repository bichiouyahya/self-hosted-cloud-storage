## Project Overview :
This project started as a fun personal lab initiative to explore secure self-hosted infrastructure and remote access architecture.
Designed and deployed a secure self-hosted cloud storage server using Ubuntu Server, Nextcloud, and Tailscale VPN to enable secure remote access without exposing services publicly.

## Architecture :
- Ubuntu Server 24.04 LTS hosted on legacy hardware
- Local LAN network: 192.168.1.0/24
- Nextcloud deployed via Snap package
- Tailscale mesh VPN for secure remote connectivity
- No public port forwarding configured
<img width="461" height="51" alt="Untitled Diagram drawio" src="https://github.com/user-attachments/assets/703fea0c-e25b-4aed-bd62-3f5b875a318c" />

## Implementation Steps
(snippets of platform are available in the screenshot folder)

### 1. Base System Setup
- Installed Ubuntu Server 24.04 LTS on an old computer 
- Configured networking using Netplan
- Enabled OpenSSH for remote management

### 2. Nextcloud Service Deployment
```bash
sudo snap install nextcloud
```
- Accessed via internal LAN IP
- Created admin account
- Verified service persistence after reboot

### 3. Secure Remote Access
```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```
- Joined private mesh network
- Confirmed remote access to Nextcloud via Tailscale IP

## Security Considerations

- Avoided exposing Nextcloud directly to the public internet
- Used Tailscale (WireGuard-based mesh VPN) to reduce attack surface
- Encrypted peer-to-peer tunnel for all remote access
- Device-based authentication for VPN access

## Challenges & Lessons Learned (Personal)

- Resolved ACPI firmware errors on legacy hardware
- Troubleshot Netplan routing conflicts
- Evaluated WireGuard vs Tailscale trade-offs
