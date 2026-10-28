# Transfermarket — v5 expanded research catalog

An independent, bilingual (English/Arabic), static football reference with a design inspired by familiar football data portals. It is not affiliated with Transfermarkt, any club, league, federation, or player.

## Catalog size in this build

- **367 player records**, with extra emphasis on Egyptian players, youth prospects and notable European academy-age players.
- **408 club records**, including clubs listed by the Egyptian Football Association and a wider set of European clubs across major and lower divisions / historical club references.
- **63 competition records**, including Egyptian senior and youth competitions and European youth competitions.
- **32 selected historical transfer records**, including the user-reported Manuel Remon → New Malden Town entry.

These counts are directory records, not a claim that every player or club in Europe or Egypt is covered. This is a large research catalog, not a complete global registry or live feed.

## Accuracy and sourcing

- Egyptian club directory reference: https://www.efa.com.eg/ar/أندية/ (the federation's club directory). It includes clubs across divisions; the club's current division must be checked before publication.
- Egyptian Professional Clubs Association: https://www.egyptianproleague.com/league (current league participants and official league context).
- football-data.org coverage and API documentation: https://www.football-data.org/coverage and https://www.football-data.org/documentation/api. Coverage and squad/statistics access depend on plan and API credentials.
- Open football data map: https://github.com/withqwerty/open-football. It lists datasets and their licenses; check each dataset's terms before reusing data.
- Topbin open football database: https://github.com/Ashborn-047/topbin. Review the repository's license, provenance and individual data files before importing.
- Wikipedia biography pages are used as research links for many stable identity entries; a link is not proof that every field has been checked. Prefer official club, league, federation or competition sources where available.
- Transfermarkt may be used as a manual research reference when appropriate, but do not scrape or republish its database without permission.

## Important limitations

1. **This is not a fully verified database.** The records include sources or research links, but many need a human fact-check before public release.
2. Current club, contract, squad status, market value, appearances, goals, assists, season statistics and current competition participation are intentionally blank unless checked.
3. Club entries identify clubs / historical references. They do not automatically assert current league membership or that the club currently fields a senior professional side.
4. Youth player lists are research leads. Youth-team membership changes quickly and must be confirmed through official academy/club lists. Do not infer current age-group status from the name being included here.
5. Transfer entries are selected historical research leads. Transfer fees are blank unless independently verified.
6. Manuel Remon's New Malden Town move is recorded as user-reported. The linked FA Full-Time page identifies a team, but does not independently verify Manuel's registration, transfer or fee. The previous club is unspecified and the fee/market value remain unknown.
7. No images, badges or proprietary branding have been copied into this package.

## Publishing on GitHub Pages (save this for later)

1. Download the ZIP and choose **Extract All**.
2. Create a **Public** repository at https://github.com/new, e.g. `global-football-index`.
3. Open the repository and choose **Add file → Upload files**. Upload the **contents** of the `global-football-index-pro` folder, so `index.html` is in the repository root, not inside a second folder.
4. Click **Commit changes**.
5. Go to **Settings → Pages**. Under Build and deployment, choose **Deploy from a branch**, select branch `main` and folder `/(root)`, then **Save**.
6. Wait for deployment. The URL usually looks like `https://YOUR-USERNAME.github.io/global-football-index/`.
7. Test the homepage, player directory, club directory, competitions, transfers and Arabic language toggle.
8. Replace the `YOUR-GITHUB-USERNAME` placeholder in `sitemap.xml` and `robots.txt` with the real GitHub Pages URL, then submit the sitemap in Google Search Console.

## Player photos and Manuel Remon profile

- The directory now supports player photos without changing the existing player dataset. Add an `imageUrl` field to a player record only when you have a suitable, permitted image URL and a source to document it.
- For records whose biography link is a Wikipedia page, the site attempts to load that page’s lead thumbnail when the player row/profile is visible. This is best-effort and depends on Wikipedia availability and the page actually having a suitable thumbnail.
- Manuel Remon has a dedicated SEO page at `manuel-remon.html`; it uses the existing profile record and links to the publicly listed photo on the existing Neocities site. If the image URL stops working, initials remain as a fallback.
- A player image appearing online does not automatically mean it can be republished freely. Prefer official/licensed sources or images with a reuse license, and record the source/credit.

## How to keep expanding it

- Add records to `data/players.json`, `data/clubs.json`, `data/competitions.json` and `data/transfers.json`.
- Preserve unique IDs. Keep unknown fields `null`, not invented values.
- For each new record, include a source URL, a review status and a last-reviewed date once a human has checked it.
- Use licensed APIs or explicitly reusable datasets for large imports; check attribution, license, commercial-use restrictions, image rights, and API quotas.
- This static site does not automatically update itself. Current squads, market values and season statistics require a lawful data source and a scheduled/manual refresh process.


## Import full 2026/27 top-five-league squads

This project includes `import-top5-squads.mjs`, a Node.js importer for the current squad pages at FootballSquads. With internet access, run it from this project folder:

```bash
node import-top5-squads.mjs
```

It creates `data/top5-squads-2026-27.json` and `data/top5-squads-import-report.json`. The website automatically merges that file into the player directory if it exists. The importer keeps source links and does not invent market values, appearances, goals, or Arabic transliterations. The source's coverage can change; check the report for failed teams.


## Top-five squads import (2026/27)
The file `data/top5-squads-2026-27.json` is loaded alongside the original catalog. Player-club duplicates are collapsed using normalized player name + club. Club records from `data/top5-league-clubs-2026-27.json` are merged into the club directory. Player and club thumbnails are attempted through Wikipedia when available; initials remain as a fallback, and not every person or crest is guaranteed to have an image.

Run locally from this folder with `npx -y http-server -p 8000`, then open `http://127.0.0.1:8000`. Do not open `index.html` directly as a `file://` URL.
