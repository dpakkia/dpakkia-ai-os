# dpakkia-ai-os

Minimal immutable Sway desktop controlled by a local LLM agent, built as a [BlueBuild](https://blue-build.org) custom OS image.

## What's in it

Base image: `ghcr.io/wayblueorg/sway`

- **Desktop**: Sway, sddm, waybar, foot, fuzzel, mako, wl-clipboard, grim, slurp, ydotool
- **Media**: pipewire-utils, wireplumber, ffmpeg, playerctl
- **Runtime**: python3, python3-pip, python3-requests, distrobox, podman
- **Browser**: Firefox
- **Shell tools**: bash, curl, jq, git, nano, htop, fastfetch

Full package list and module config: [`recipes/recipe.yml`](recipes/recipe.yml).

## Builds

- **GitHub Actions** (`.github/workflows/build.yml`) — builds and pushes the image daily at 06:00 UTC, on every push to `main`, and on manual dispatch. Images are signed with cosign; the public key is checked in as [`cosign.pub`](cosign.pub).
- **GitLab CI** (`.gitlab-ci.yml`) — mirrors the same build using the `blue-build/cli` image.

## Usage

Rebase an existing bootc-based system onto this image:

```bash
bootc switch ghcr.io/dpakkia/dpakkia-ai-os:latest
```

Verify image signatures against the included public key:

```bash
cosign verify --key cosign.pub ghcr.io/dpakkia/dpakkia-ai-os:latest
```

## License

Apache-2.0 — see [LICENSE](LICENSE).
