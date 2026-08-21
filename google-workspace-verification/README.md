# Google Workspace for Nonprofits — domain verification fix

**Organisation:** Verein für buddhistische Praxis und Gemeinschaft e.V.
**Domain:** buddhistische-praxis-gemeinschaft.de
**Rejection:** "the connection between [the organisation] and [the domain] couldn't be verified"

---

## What Google is actually asking for

This is **not** the DNS verification you do inside the Workspace admin console (the
`google-site-verification` TXT record). That one proves you *control* the domain, and it comes
later. This rejection comes from the **nonprofit eligibility review**, where a human opens your
website and looks for the organisation's registered legal name. They searched for
*"Verein für buddhistische Praxis und Gemeinschaft e.V."* on
buddhistische-praxis-gemeinschaft.de and could not establish the link.

Their own hint says it plainly: put text on the domain that identifies the organisation behind
it. In Germany there is a purpose-built page for exactly that — the **Impressum**.

## Most likely causes, in order

1. **No Impressum, or one that names a private person instead of the e.V.** By far the most
   common cause. A reviewer who finds no legal entity anywhere on the site has nothing to verify.
2. **The site uses a short or informal name only** — e.g. "Buddhistische Praxis & Gemeinschaft",
   a centre name, or a dharma-group name — and never the full registered form with the `e.V.`
   suffix. The reviewer matches against the name on your registration documents, character for
   character.
3. **The site is a placeholder / under construction / behind a login.** Nothing to review.
4. **Name mismatch with your validation record.** In Germany, Google's nonprofit eligibility check
   normally runs through **Stifter-helfen (Haus des Stiftens)**, TechSoup's German partner. If the
   organisation record there carries a different spelling or lists a different website, that
   mismatch alone can produce this rejection — worth checking your account there.
5. **`.de` WHOIS shows nothing.** DENIC does not publish registrant data, so Google cannot confirm
   ownership that way even if the domain *is* registered to the Verein. This is why the on-site
   evidence carries all the weight.

> I could not open https://www.buddhistische-praxis-gemeinschaft.de/ from this environment — the
> session's network policy blocked the request (403 at the egress proxy). So causes 1–3 above are
> ranked from experience, not from an inspection of your live site. Check which one applies before
> you reply to Google.

## Fix, in order

### 1. Publish an Impressum at `/impressum`
Use `impressum.html` (standalone page) or `impressum-zum-einfuegen.txt` (paste into Wix,
WordPress, Jimdo, IONOS, Squarespace). Replace every `[[...]]`.

The paragraph that does the actual work for Google is *"Betreiber dieser Website und Inhaber der
Domain"* — it names the association and the domain in one sentence. Do not delete it.

Link the page from the main navigation **and** the footer. This is a legal requirement in Germany
(§ 5 DDG) regardless of Google, so it is worth doing properly.

### 2. Put the legal name in the footer of every page
Use `footer-snippet.html`. The reviewer may only look at the homepage — the full registered name
should be visible there without clicking anything.

### 3. Name the association on the homepage / "Über uns"
One sentence in the body text is enough, e.g.:

> Träger dieser Website ist der **Verein für buddhistische Praxis und Gemeinschaft e.V.**,
> eingetragen im Vereinsregister des Amtsgerichts [[ORT]] unter VR [[NUMMER]].

### 4. Check the pages are actually reachable
- [ ] `https://www.buddhistische-praxis-gemeinschaft.de/impressum` opens in a private window, no login
- [ ] Both `www.` and the bare domain resolve and serve the site
- [ ] Valid HTTPS certificate, no browser warning
- [ ] The page is not `noindex` and not disallowed in `robots.txt`
- [ ] The exact string `Verein für buddhistische Praxis und Gemeinschaft e.V.` appears in the
      page source — spelled exactly as on the register extract, including `e.V.`
- [ ] Give Google a day or two after publishing before replying, so caches and crawls catch up

### 5. Reply to Google
Use `antwort-an-google.md` (English and German versions). Attach the Vereinsregisterauszug and the
Freistellungsbescheid. Reply on the original email thread so the case history stays attached.

## Files here

| File | Purpose |
|---|---|
| `impressum.html` | Complete standalone Impressum page (§ 5 DDG, § 18 Abs. 2 MStV) |
| `impressum-zum-einfuegen.txt` | Same content as plain text, for pasting into a CMS editor |
| `footer-snippet.html` | Identity footer for every page + schema.org `Organization` markup |
| `antwort-an-google.md` | Reply email drafts (EN + DE) and the attachment checklist |

## Before you publish

Every `[[...]]` is a gap I could not fill — address, board members, register court, VR number,
Finanzamt details, contact email. Find them all with:

```sh
grep -rn '\[\[' google-workspace-verification/
```

Two content notes:

- The **USt-IdNr.** block only belongs there if the Verein actually has one. Most small
  associations do not — delete the block rather than leaving it blank.
- Older Impressum templates still carry a link to the EU online dispute resolution platform
  (`ec.europa.eu/consumers/odr`). That platform has been discontinued; the drafts here leave it
  out deliberately. Don't paste it back in from an older template.

This is a standard Impressum structure, not legal advice — if the Verein has a lawyer or a
Dachverband (e.g. the Deutsche Buddhistische Union), a quick read-through before publishing costs
nothing.
