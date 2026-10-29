# waystationhealth.com

The Waystation Health site. Five static files, no build step, no dependencies. Open `index.html` in a browser and it runs.

Hallmark pass 2026-10-29 on theme Furrow: 75 FAIL / 49 REFLEX down to 0 / 0.

| File | Role |
|---|---|
| `index.html` | Waystation Health |
| `myabuela.html` | myabuela.com |
| `tokens.css` | Furrow tokens |
| `base.css` | element defaults |
| `style.css` | page rules. The Hallmark stamp has to stay on the first non-empty line |
| `.hallmark/` | gate log and `compare.html`, before and after |

## Nothing confidential goes in here

This repo is public, because that is what makes Pages free. The investment memo, the entity structure memo, the SBA affiliation analysis, the compliance flowchart and the deck stay in the private `claude-outputs` repo and in Google Drive. Nothing that names a customer, a partner or a certification number belongs in a file in this repo.

## Deploying

Every push to `main` publishes. The workflow refuses to deploy when any of the five files is missing or when `style.css` no longer opens on the Hallmark stamp, so a half-synced folder cannot take the live site down to a 404.

Pages enables itself on the first successful run, so there's nothing to switch on by hand.

## DNS

`CNAME` in this repo claims the apex domain. The domain is registered with Squarespace, so the records change in Squarespace DNS and the registration stays where it is.

Apex `waystationhealth.com`, four A records:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

And `www` as a CNAME to `bdo811.github.io`.

Confirm that list against what the repo's Settings > Pages panel shows before changing anything, since GitHub has moved these addresses before. Delete the Squarespace parking records for the apex at the same time, or the domain keeps resolving to the parking page.

Pages issues the certificate once DNS resolves, which takes some minutes. Turn on Enforce HTTPS after it does.

## Rebuilding the Squarespace bundle

If the site ever does go to Squarespace instead, `build_squarespace.py` in the `claude-outputs` repo flattens these five files into a standalone page and a Code Block fragment.
