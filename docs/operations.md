# Operations notes: Maintaining self-hosted services

## Current environment

A UGREEN NAS hosts Docker-based services including Jellyfin, Calibre, and Calibre-Web. I administer the environment using Linux command-line tools and SSH and use Tailscale for private remote connectivity.

## Operational themes

- **Container lifecycle:** Understand how services are started, updated, restarted, and configured.
- **Persistent data:** Separate application configuration and collections from disposable containers.
- **Troubleshooting:** Verify networking, ports, permissions, and application behavior independently.
- **Access boundaries:** Prefer authenticated private connectivity for personal services.

## Documentation to add after verification

- A sanitized service inventory with verified port mappings
- Backup and restoration tests, including recovery objectives
- Update and rollback procedures
- Health checks and monitoring
- Accessibility and usability observations

These are documentation goals.
