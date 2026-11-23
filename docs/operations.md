# Operations notes: Maintaining self-hosted services

## Current environment

A UGREEN NAS hosts Docker-based services including **Jellyfin and Calibre-Web, both used by a small community**, and **Calibre, whose backend I administer**. I administer the environment using Linux command-line tools and SSH and use Tailscale for private remote connectivity.

## Operational themes

- **Container lifecycle:** Understand how services are started, updated, restarted, and configured.
- **Persistent data:** Separate application configuration and collections from disposable containers.
- **Troubleshooting:** Verify networking, ports, permissions, and application behavior independently.
- **Access boundaries:** Maintain appropriate authentication and access boundaries for community-facing services.

## Documentation to add after verification

- A sanitized service inventory with verified port mappings
- Backup and restoration tests, including recovery objectives
- Update and rollback procedures
- Health checks and monitoring
- Accessibility and usability observations

These are documentation goals.
