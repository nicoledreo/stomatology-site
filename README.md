# Stomatology site — template build

A six-page static site for a dental practice, built as a **template**. It is not any real
practice's website and it is not ready to be one.

## Read this before you use it for anything

**Every business value on these pages is a placeholder.** The practice name, the town, the
street address, the telephone number, the email address, the opening hours, the three staff
names with their roles, and the four service names are all invented. So are the photographs —
they are generated images, not photographs of a real premises, and none of them shows an
identifiable person.

The invented values are deliberately drawn from reserved forms that cannot collide with a real
business: the email uses the `.example` TLD reserved by RFC 2606, and the telephone uses the
555-01xx range reserved for fiction.

Nothing on the site claims a rating, a review, an award, a certification, a price, a patient
count, or a clinical outcome. No protected clinical title is used for any named person — the
three roles are Practice Manager, Treatment Coordinator and Reception Lead, all functional and
none register-gated.

## Why it is not indexed

Every page carries `<meta name="robots" content="noindex">` and `robots.txt` disallows all
crawling. A search engine that indexed these pages would publish a dental practice that does
not exist, at an address that does not exist, with a telephone number nobody answers.

## Turning it into a real practice's site

Three things happen together, or not at all:

1. Fill every placeholder. They are indexed by an HTML comment marker in the authored source:
   `grep -rn "<!-- swap:" .` in the build tree returns every slot. The marker names are never
   renamed, because a stale grep returns zero hits and zero hits reads exactly like "all done".
2. Remove the `noindex` meta from all six pages.
3. Change `robots.txt` from `Disallow` to `Allow`, and repoint `sitemap.xml` at the real domain.

Doing any one without the others either hides a finished site or publishes a fabricated one.

## What is in here

```
index.html  services.html  about.html  team.html  faq.html  contact.html
design-system/    the six stylesheets the pages link
assets/           28 images plus the favicon
sitemap.xml  robots.txt
```

Self-contained: every stylesheet, image and internal link resolves inside this directory, with
no build step and no external dependency other than the web fonts. Verified before publishing —
304 local references and 108 in-page anchors, all resolving.
