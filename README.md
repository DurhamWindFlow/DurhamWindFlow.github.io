# Durham WindFlow — group website

Source for **[durhamwindflow.github.io](https://durhamwindflow.github.io)**, the website of
Durham WindFlow, the Atmospheric Flow and Wind Energy Dynamics Group at Durham University.

Built with Jekyll on GitHub Pages. No theme, no JavaScript framework, no build step to run
locally unless you want one.

---

## ⚠️ Where the content lives

**Do not edit people, publications or research themes in this repository.** They live in
[`DurhamWindFlow/.github`](https://github.com/DurhamWindFlow/.github) under `Profile/data/`,
and are copied here automatically:

| Edit this, in the `.github` repo | It becomes |
|---|---|
| `Profile/data/people.yml` | the [People](https://durhamwindflow.github.io/people/) page, and `Profile/people.md` on the org page |
| `Profile/data/publications.yml` | the [Publications](https://durhamwindflow.github.io/publications/) page, and the table in the org README |
| `Profile/data/projects.yml` | the [Research](https://durhamwindflow.github.io/research/) page and the home page cards |
| `Profile/data/site.yml` | group name, blurbs, contact details, role tiers, open positions |
| `Profile/Images/` | member photographs |

Anything in `_data/` and `assets/img/people/` here is **overwritten on every sync** — changes
made to those directories by hand will be silently lost.

### How the sync works

[`.github/workflows/sync-content.yml`](.github/workflows/sync-content.yml) clones the public
`.github` repository, copies the four YAML files and the photos across, sanity-checks them, and
commits only if something changed. It runs **hourly**, needs **no tokens or secrets**, and can be
run on demand from the **Actions → Sync content from .github → Run workflow** button when you
want an edit live immediately.

*Optional:* to make every push to `.github` propagate within a minute instead of within the hour,
create a fine-grained PAT with `Actions: write` on this repository and save it in the `.github`
repository as the secret `SITE_SYNC_TOKEN`. The dispatch step is already wired up and simply
skips itself when the secret is absent.

---

## Adding someone to the People page

1. Put a square-ish photo in `Profile/Images/` in the `.github` repo (e.g. `Firstname.jpg`).
2. Copy the commented template at the bottom of `Profile/data/people.yml` and fill it in.
3. Commit.

The org page regenerates immediately; the website follows within the hour, or straight away via
the Run workflow button. Nothing in *this* repository needs touching.

To add a **new field of expertise**, add the term to `site.yml → expertise` first, then reference
its key from the person's entry.

---

## Repository layout

```
_config.yml                     Jekyll config, nav, site metadata
_layouts/default.html           The single page shell
_includes/person-card.html      One person
_includes/pub-item.html         One publication
assets/css/main.css             The entire stylesheet
index.html                      Home
research.html  people.html  publications.html  contact.html
_data/                          SYNCED — do not edit
assets/img/people/              SYNCED — do not edit
.github/workflows/sync-content.yml
```

## Running it locally

Optional — the site builds fine on GitHub Pages without this.

```bash
gem install bundler jekyll
jekyll serve
```

Then open <http://localhost:4000>.

## Licence

MIT — see [LICENSE](LICENSE). Member photographs remain the property of the individuals concerned.
