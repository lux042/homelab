# Home Lab | Infrastructure for Accessible Knowledge

**Self-hosted infrastructure centered on accessible resources, digital independence, and responsible data stewardship.**

I build and maintain a personal home lab to explore how practical infrastructure decisions can make digital resources easier to organize, preserve, and access. My work combines Linux administration, containerized applications, private networking, and digital library services with a broader interest in community-centered technology.

This is a **private, personal learning environment**, not a public library or community-facing production service. Its architecture and design principles are relevant to educational institutions, libraries, nonprofits, and other organizations working to make information more accessible.

## At a glance

| Area | Implementation | Engineering focus |
| --- | --- | --- |
| Host | UGREEN NAS | Storage, administration, service hosting |
| Containers | Docker | Deployment, isolation, persistent volumes |
| Digital library | Calibre and Calibre-Web | Collection organization and multi-device access |
| Media | Jellyfin | Self-hosted media management |
| Private connectivity | Tailscale | Encrypted access across trusted devices |
| Secure web access | Tailscale Serve (HTTPS) | Reverse proxy and service exposure boundaries |
| Operations | Linux, SSH | Configuration, diagnosis, maintenance |

## Why this project exists

Access to information depends on more than an application interface. It also depends on storage, network availability, maintainability, portability, and the choices made about who controls data. I use my home lab to understand these foundations firsthand and to practice building services that prioritize users rather than platform lock-in.

My guiding principles:

- **Accessibility:** Make authorized personal resources convenient to access across devices.
- **Stewardship:** Treat digital collections as resources worth organizing and preserving.
- **Independence:** Understand and control the infrastructure supporting those resources.
- **Privacy and security:** Favor authenticated private access over unnecessary public exposure.
- **Transferable learning:** Document approaches that could inform future library, education, and community technology work.

## Architecture

See [the architecture overview](architecture/README.md) for a diagram and trust-boundary notes. The diagram is intentionally conceptual; it excludes private addresses, credentials, and internal host details.

```mermaid
flowchart TD
    Devices[Authorized personal devices] -->|Encrypted private connectivity| Tail[Tailscale tailnet]
    Tail --> NAS[UGREEN NAS / Linux host]
    NAS --> Docker[Docker services]
    Docker --> Calibre[Calibre content server]
    Docker --> Web[Calibre-Web]
    Docker --> Jellyfin[Jellyfin]
    Tail -->|Tailscale Serve / HTTPS| Web
    NAS --> Storage[(Persistent storage)]
    Docker --> Storage
```

## Technical case studies

### 1. A self-hosted digital library

I deployed Calibre and Calibre-Web as containerized services on my NAS, using persistent storage to manage a personal ebook collection. This project involved distinguishing the Calibre content server from the Calibre-Web frontend, configuring container ports and volumes, and testing connectivity.

**Skills demonstrated:** Docker configuration, persistent volumes, service architecture, troubleshooting, and digital collection management.

[Read the case study](docs/digital-library.md)

### 2. Private remote access with HTTPS

I connected trusted devices through Tailscale and configured Tailscale Serve to proxy Calibre-Web over HTTPS within my private tailnet. This provided a practical lesson in service binding, container networking, encrypted access, and the difference between local service ports and externally reachable endpoints.

**Skills demonstrated:** Private networking, Linux CLI, SSH, reverse proxies, HTTPS, and security boundaries.

[Read the case study](docs/private-access.md)

### 3. Media services and operational ownership

I operate Jellyfin in Docker as part of my self-hosted environment. Maintaining the service alongside other applications provides hands-on experience with container lifecycle management and the operational tradeoffs of managing resources independently.

**Skills demonstrated:** Container operations, Linux administration, and application maintenance.

[Read the operations notes](docs/operations.md)

## Tools and technologies

**Docker · Linux · SSH · Tailscale · HTTPS · Reverse proxying · NAS storage · Jellyfin · Calibre · Calibre-Web · Networking / DNS**

## Security and documentation approach

This repository documents architecture and lessons learned, **not live credentials or deployable copies of my private configuration**. Sensitive addresses, host identifiers, authentication details, API keys, and personal media or book collections are intentionally excluded. Any example configuration must use placeholders.

## Roadmap

- [x] Deploy multiple containerized services on a NAS
- [x] Establish private access using Tailscale
- [x] Configure HTTPS access to Calibre-Web through Tailscale Serve
- [x] Document core architecture and technical case studies
- [ ] Add sanitized, reproducible Docker Compose examples
- [ ] Document a tested backup and recovery procedure
- [ ] Add monitoring and service-health documentation
- [ ] Explore an authorized, public-domain digital commons prototype

## Related projects

- [sunBEAR](https://github.com/lux042/sunBEAR) — cross-platform archival research tooling
- [Pocket sunBEAR](https://github.com/lux042/pocket-sunBEAR) — mobile research collection and exports
- [JFK Reader](https://github.com/lux042/JFK-Reader) — document retrieval and question-answering across archival records
- [Forage](https://github.com/lux042/forage) — location-aware restaurant discovery and journaling

---

Built and documented by [lux042](https://github.com/lux042). This repository is a portfolio of a personal environment and is not an invitation to access the services it describes.