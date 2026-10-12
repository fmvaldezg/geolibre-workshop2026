# GeoLibre: GIS in your browser

Slides for a one-hour introductory workshop on [GeoLibre](https://geolibre.app), built with [Slidev](https://sli.dev) and published with GitHub Pages.

The deck lives in [`GeoLibre_intro2026/`](./GeoLibre_intro2026). Edit [`slides.md`](./GeoLibre_intro2026/slides.md) to change the content.

## Run it locally

Requires Node.js 22.12 or later (20.19 and later in the 20 line also works).

```bash
cd GeoLibre_intro2026
npm ci
npm run dev
```

Then open <http://localhost:3030>. Press `o` for the slide overview and `p` for presenter mode with speaker notes.

Use `npm ci`, not `npm install`. It installs the exact versions recorded in `package-lock.json`, which are the ones this deck is known to build with.

## Publish with GitHub Pages

1. Create a repository on GitHub and push this folder to its `main` branch.
2. In the repository, open **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Every push to `main` runs `.github/workflows/deploy.yml`, which builds the deck and publishes it at `https://<user>.github.io/<repository>/`.

The workflow reads the repository name for the site's base path, so the repository can have any name.

## What is in the folder

| Path | What it is |
| --- | --- |
| `GeoLibre_intro2026/slides.md` | The slides and the speaker notes |
| `GeoLibre_intro2026/style.css` | Colors and shared styles for the whole deck |
| `GeoLibre_intro2026/components/StepTag.vue` | The "Step 2 of 6" progress marker on the hands-on slides |
| `GeoLibre_intro2026/components/DataFile.vue` | The download buttons for the sample data |
| `GeoLibre_intro2026/public/assets/` | Images. `cover.svg` is the title background |
| `GeoLibre_intro2026/public/data/` | Sample data that attendees download from the slides |
| `.github/workflows/deploy.yml` | Build and publish to GitHub Pages |

## Things you may want to change

- **Screenshots.** Four slides load screenshots from the GeoLibre documentation site (`assets.geolibre.app`). To use your own, save them in `GeoLibre_intro2026/public/assets/` and change the `image:` line at the top of the slide to `/assets/your-file.png`.
- **Analytics.** The workflow adds a Google Analytics tag to the published site. The measurement ID is the `GA_ID` value near the top of `deploy.yml`. Set it to `''` to publish without analytics.
- **Folder name.** If you rename `GeoLibre_intro2026`, update `DECK_DIR` in `deploy.yml` to match.

## Sample data and credits

- `philadelphia-neighborhoods.geojson` and `philadelphia-neighborhoods.zip` (zipped Shapefile): Philadelphia neighborhood boundaries from the OpenDataPhilly [open-geo-data](https://github.com/opendataphilly/open-geo-data) repository, attributed to Abaca Labs, released under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- `philly_landmarks.csv`: 19 Philadelphia landmarks with approximate coordinates, prepared for this workshop.
- GeoLibre is developed by Qiusheng Wu and contributors under the MIT license.
