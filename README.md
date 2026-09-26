# yolks

Docker images for Pterodactyl/Pelican eggs used by Empire War.

Based on [Ptero-Eggs/yolks](https://github.com/Ptero-Eggs/yolks).

## Images

| Image | Base | Pull |
| --- | --- | --- |
| MongoDB 8.0 | `mongo:8.0-noble` | `ghcr.io/empirewar/yolks:mongodb_8.0` |
| Valkey 9.1 | `valkey/valkey:9.1-alpine` | `ghcr.io/empirewar/yolks:valkey_9.1` |

`mongo:8.0-noble` is a floating tag that always resolves to the latest MongoDB
8.0.x release on Ubuntu Noble. The build workflow reruns weekly (Mondays 00:00
UTC) so the published image picks up new 8.0.x patch releases automatically.

`valkey/valkey:9.1-alpine` works the same way for Valkey 9.1.x. The image runs
under `tini -g` with `SIGINT` as stop signal, so a `^C` stop command in the egg
makes Valkey save and shut down cleanly.
