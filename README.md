# The Ascent — Platonic Fathers, Quote of the Day

A daily reading from the Church Fathers where the Platonic inheritance is
visible — participation, logos, ascent, apophasis, divinization, and Mary
as *chora*. Static site, no backend, deterministic daily selection.

## How the daily pick works (the interesting part)

- **Historical arc, not shuffle**: quotes are ordered Philo → Clement →
  Origen → Athanasius → … → Damascene. Each day walks one step up the
  ladder; the cycle repeats when it completes. The app *is* an
  itinerarium.
- **Deterministic**: the day number since launch indexes the ordered
  list. No server, no state — every visitor sees the same quote, and
  yesterday is reproducible.
- **Liturgical overlay**: fixed feasts (Assumption, Christmas,
  Annunciation…) override with a themed pick from the matching tag pool;
  Lent (computed via the standard Easter algorithm) biases toward
  apophasis/ascent every third day.
- **The ladder widget** at the bottom shows which rung of the ascent
  today's author occupies.

## Ship checklist

1. **Verify quotes** — see `VERIFICATION.md`. The seed was curated from
   familiarity, not open copies. Unverified translations show a dotted
   red underline on the site until the `(VERIFY)` flag is removed from
   the JSON.
2. Create a GitHub repo, push these files.
3. Settings → Pages → Source: "Deploy from a branch" → `main` / root.
4. Site is live at `https://<you>.github.io/<repo>/` in ~1 minute.
5. Later: custom domain (`wbbcctv.com`) in the Pages settings + a CNAME
   at GoDaddy → free automatic Let's Encrypt TLS. Watch the cert appear:
   `openssl s_client -connect wbbcctv.com:443 -servername wbbcctv.com`

## Local preview

```bash
python3 -m http.server 8080
# then http://localhost:8080 — opening index.html directly won't work
# (fetch of quotes.json requires http, not file://)
```

## The Librarian (future)

`.github/workflows/librarian.yml` is a stub for the weekly curation
agent: propose quotes → fetch the cited source → verify the text appears
→ open a PR. AI curates, a human gates, the site serves only merged
data. Enable it when ready (instructions in the file).

## Editing content

- `quotes.json` — the corpus. `_meta` holds the curation principle;
  `concept_tags` is the taxonomy. Add quotes anywhere; the arc ordering
  is derived from the author name at render time.
- Launch date for the cycle: `LAUNCH` constant in `index.html`.
