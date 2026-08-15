# yolks

Docker images for Pterodactyl/Pelican eggs used by Empire War.

Based on [Ptero-Eggs/yolks](https://github.com/Ptero-Eggs/yolks).

## Images

| Image | Base | Pull |
| --- | --- | --- |
| MongoDB 8.0 | `mongo:8.0-noble` | `ghcr.io/empirewar/yolks:mongodb_8.0` |

`mongo:8.0-noble` is a floating tag that always resolves to the latest MongoDB
8.0.x release on Ubuntu Noble. The build workflow reruns weekly (Mondays 00:00
UTC) so the published image picks up new 8.0.x patch releases automatically.
