# Case study: Digital library infrastructure

## Problem

I wanted a digital library infrastructure that could support organized, accessible collections for authorized users while maintaining control of the underlying files and services.

## Approach

I deployed Calibre and Calibre-Web using Docker on a UGREEN NAS. Calibre provides collection management and a content server; Calibre-Web offers a browser-oriented interface. Their different service roles required attention to port mappings, container configuration, and shared book storage.

## Engineering lessons

- A working container does not guarantee a reachable service: host ports, container ports, and application behavior must all align.
- Persistent storage is essential for keeping collections and settings independent of container lifecycle.
- Clear distinctions between the library management backend and browser-facing frontend simplify troubleshooting.

## Outcome

I established connectivity to the Calibre services and configured access to Calibre-Web. The documented implementation supports digital collection access. The repository does not yet specify the community's access model, lending permissions, or content licensing.

## Next steps

Document sanitized Compose configurations, a tested backup/restore procedure, and accessibility considerations for the web interface.
Interested in building a rig to for physical media scanning.
