# Nico's Premium Details — Clone

A mirror of [nicospremiumdetails.framer.website](https://nicospremiumdetails.framer.website/),
including the prerendered HTML for every route plus the Framer runtime modules, images, and CMS
data, all served from this repository's subpath.

Live: https://ari-builds.github.io/nicospremiumdetails-clone/

## Routes

| Path | Page |
| --- | --- |
| `/` | Home |
| `/about-us` | About Us |
| `/car-detailing` | Car Detailing |
| `/ceramic-coating` | Ceramic Coating |
| `/contact` | Contact |
| `/headlight-enhancement` | Headlight Enhancement |
| `/membership` | Membership |
| `/odor-removal` | Odor Removal |
| `/services-page` | Services |

Each route is a real directory containing its own `index.html` (Framer's prerendered output), so
navigation is a plain page load rather than client-side routing.

## Hosting notes

Three patches make a Framer export work on a static project site:

1. `framerusercontent.com` asset URLs were rewritten to `/nicospremiumdetails-clone/...`.
2. `new URL(rel, "<path>")` bases were made absolute with `location.origin`, since a relative
   base throws `Invalid base URL`.
3. Framer's CMS loader requests byte ranges via `?range=`, which static hosts ignore. A
   client-side slice fallback was added so the loader accepts the full-file response.

Deployment is handled by `.github/workflows/deploy.yml`.
