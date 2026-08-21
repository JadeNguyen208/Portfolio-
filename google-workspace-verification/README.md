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

## What the DNS actually shows (checked 2026-08-21)

| Record | Value | Meaning |
|---|---|---|
| `buddhistische-praxis-gemeinschaft.de` **A** | `46.38.243.234` | A netcup server — **not** the website |
| `www.buddhistische-praxis-gemeinschaft.de` **CNAME** | `buddhistische-praxis-de.web.app` → `199.36.158.100` | Firebase Hosting — the real site |
| **MX** | `SMTP.GOOGLE.COM` (pref 1) | Google Workspace mail is already configured |
| **TXT** | `google-site-verification=XzC9Oi-p3d_kBRxsXPkQR4hKHFTTQmejYEnshv1kvtM` | Domain ownership for Google is already verified |
| **NS** | `netcup.firstns.cc`, `.secondns.at`, `.thirdns.de`, `.fourthns.systems`, `.fifthns.com` | DNS is managed at netcup |

**The apex domain and `www` point at two different servers.** Only `www.` serves the Firebase
site. The bare domain goes to netcup, which almost certainly shows a parking or default page —
and it may not even have a valid TLS certificate for this domain.

This matters because Google's rejection email names the domain **without** `www`:
*"…the connection between Verein für buddhistische Praxis und Gemeinschaft e.V. and
buddhistische-praxis-gemeinschaft.de couldn't be verified."* If the reviewer opened the bare
domain, they never saw the website at all.

Note also what is **already done**: the `google-site-verification` TXT record and the Google
Workspace MX record are both in place on the apex domain. So domain *ownership* verification is
not the problem, and adding `www` anywhere is not the fix — see below.

## Does `www` need to be added for verification?

No — and it is the wrong direction.

* **Google Workspace / admin console** uses the **bare domain**,
  `buddhistische-praxis-gemeinschaft.de`. Google treats `www.` as a separate subdomain. Mail
  addresses are `name@buddhistische-praxis-gemeinschaft.de`. The verification TXT record belongs
  on the apex, where it already is.
* **The nonprofit eligibility review** is a human opening the website. What is needed is not a
  `www` prefix but that **both** addresses show the same site, with the association's legal name
  on it.

So the fix is the opposite: make the **apex** serve the site that `www` already serves.

## Most likely causes, in order

1. **The apex domain does not serve the website** (evidence above). The reviewer opens
   `buddhistische-praxis-gemeinschaft.de`, lands on a netcup placeholder, and finds no
   organisation at all. This is now the leading explanation.
2. **No Impressum, or one that names a private person instead of the e.V.** Even on the `www`
   site, a reviewer who finds no legal entity has nothing to verify.
3. **The site uses a short or informal name only** — e.g. "Buddhistische Praxis & Gemeinschaft" —
   and never the full registered form with the `e.V.` suffix. The reviewer matches against the
   name on your registration documents, character for character.
4. **Name mismatch with your validation record.** In Germany, Google's nonprofit eligibility check
   normally runs through **Stifter-helfen (Haus des Stiftens)**, TechSoup's German partner. If the
   organisation record there carries a different spelling or lists a different website, that
   mismatch alone can produce this rejection — worth checking your account there.
5. **`.de` WHOIS shows nothing.** DENIC does not publish registrant data, so Google cannot confirm
   ownership that way even if the domain *is* registered to the Verein. This is why the on-site
   evidence carries all the weight.

> I could not open the site itself from this environment — the session's network policy blocks
> that host (403 at the egress proxy). The DNS facts above are measured; what the two servers
> actually render is not. Open both addresses in a private window and see for yourself.

## Fix, in order

### 0. Make the apex domain serve the website
Do this first — it is the only cause with hard evidence behind it.

In the **Firebase console** → Hosting → the `buddhistische-praxis-de` site → *Add custom domain*,
add `buddhistische-praxis-gemeinschaft.de` alongside the existing `www` entry. Firebase will show
the exact **A records** to enter; replace the current `46.38.243.234` A record at **netcup** with
them. Firebase then issues a TLS certificate for the apex too.

Either serve the same content on both, or redirect the apex to `www` — either is fine, as long as
the apex no longer dead-ends at netcup.

> **Do not touch the `MX` record or the `google-site-verification` TXT record** while editing the
> zone. Those carry your Workspace mail and your domain verification. Changing an A record does not
> affect them, but netcup's domain-parking/forwarding toggles can rewrite a zone — check the MX and
> TXT records are still there afterwards.

Verify with a DNS lookup, then open `https://buddhistische-praxis-gemeinschaft.de` (no `www`) in a
private window and confirm it loads the site with a valid certificate.

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
- [ ] Both `www.` and the bare domain serve the site (see step 0 — currently they do not)
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
