# Taraksh Choudhary — personal portfolio

This repository contains the source for Taraksh Choudhary’s personal portfolio. It is a small, static website designed to be hosted directly with GitHub Pages. There is no build step, package manager, server-side code, or runtime dependency.

## What the site is

The site introduces Taraksh and presents selected projects, an achievement, and a short biography. It uses a responsive dark visual theme with CSS-created decoration and inline SVG icons. It does not use a personal photograph.

The portfolio is intended to be readable by people, search engines, assistive technologies, and AI tools that inspect public web pages. Text in the page is the source of truth; decorative graphics are not a substitute for the written descriptions.

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | Complete single-page site: markup, responsive styles, external links, metadata, and structured data. |
| `favicon.svg` | Scalable brand mark for browsers that support SVG favicons. |
| `favicon.png` | 48 × 48 PNG favicon fallback for browsers and tools that do not use SVG favicons. |
| `robots.txt` | Crawler guidance for the published site. Its sitemap URL must be updated after the final Pages URL is known. |
| `sitemap.xml` | XML sitemap for the single public page. Its URL is a setup placeholder until the Pages address is known. |
| `README.md` | Project overview, hosting and search setup, and maintenance guidance. |

Sections such as Projects, Achievements, and About are all part of `index.html`. Their `#projects`, `#achievements`, and `#about` links are in-page navigation anchors, not separate pages; do not add them as separate sitemap entries.

## Deploy with GitHub Pages

1. Put these files at the root of the GitHub repository that will host the site.
2. Push the files to GitHub.
3. Open the repository’s **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, select the branch containing the site, and select the repository root (`/`) as the folder.
5. Save the settings and wait for GitHub Pages to publish the site.
6. Open the Pages URL shown in repository settings and check that the home page, navigation, external links, and mobile layout work.

This static site does not need a GitHub Actions workflow or build command. If the repository uses a custom domain later, configure it through GitHub Pages and use that same domain consistently in the sitemap, canonical link, and Search Console property.

### Set the real public URL before submitting the sitemap

The exact GitHub Pages URL is not known yet. A user-site URL usually looks like `https://USERNAME.github.io/`. A project-site URL usually looks like `https://USERNAME.github.io/REPOSITORY/`. Use the exact URL shown in **Settings → Pages**; do not guess which form applies.

Before submitting the sitemap:

1. In `robots.txt`, replace `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/sitemap.xml` with the full address of the deployed `sitemap.xml`.
2. In `sitemap.xml`, replace `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/` with the exact public home-page URL, including the repository path for a project site. Keep the final slash.
3. In `index.html`, add a canonical link inside `<head>` after the final URL is confirmed:

   ```html
   <link rel="canonical" href="https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/">
   ```

4. Replace the sample URL in the `og:url` metadata with that same public home-page URL.
5. Commit and push the changes, wait for Pages to redeploy, then open both `https://YOUR-SITE/robots.txt` and `https://YOUR-SITE/sitemap.xml` in a browser to confirm that they are publicly accessible and contain no placeholder values.

Do not submit either template URL to a search engine. The placeholders are deliberately obvious so an unconfigured address is not mistaken for the final site.

## Google Search Console

Google Search Console account access and ownership verification must be completed by the site owner. This repository does not contain a verification token because no token has been provided.

1. Publish the site and confirm its public URL.
2. Open [Google Search Console](https://search.google.com/search-console/) and add a **URL-prefix** property for the exact published URL. For a project site, include the repository path.
3. Choose the **HTML tag** verification method. Copy the full `<meta name="google-site-verification" ...>` tag supplied by Google and place it in the `<head>` of `index.html`. Preserve the token exactly.
4. Commit and push the change, wait for GitHub Pages to redeploy, then select **Verify** in Search Console.
5. After verification, submit the full public URL to `sitemap.xml` in the Search Console **Sitemaps** report. The URL must match the `Sitemap:` address in `robots.txt`.
6. Use **URL Inspection** to request indexing of the home page if appropriate. Review indexing and crawl reports over time; inclusion and ranking are controlled by Google and are not guaranteed by this repository.

If Google provides an HTML verification file instead of a meta tag, place that exact file at the repository root and keep its filename and contents unchanged. Never commit passwords, account recovery codes, or other credentials.

## Search and crawler files

### `robots.txt`

`robots.txt` is a public set of crawl preferences, not access control. The current policy allows general crawlers to access the public site. Its `Sitemap:` directive is a placeholder until the final Pages URL is set. Do not use this file to hide private data; anything deployed to a public GitHub Pages site can be viewed directly.

### `sitemap.xml`

The sitemap lists the single canonical page. A sitemap helps crawlers discover a URL but does not force crawling, indexing, or a particular search result. Keep its `<loc>` value absolute, publicly reachable, and identical to the deployed page URL. Update `<lastmod>` only when the page receives a meaningful content update.

### Metadata and structured data

`index.html` provides a page title, description, author, crawler directive, Open Graph and X/Twitter summary metadata, and JSON-LD `Person` structured data. A canonical URL and `og:url` are intentionally left for configuration after the Pages URL is known. There is no social sharing image because the site intentionally has no personal photo or supplied preview image.

Structured data should describe information that is also visible and accurate on the page. Keep social profile URLs in JSON-LD aligned with the actual profile links. Do not add a location, contact information, age, or other personal details unless Taraksh explicitly asks for them.

## Content and links

- **Projects:** Word Flow, Excel Flow, and Taraksh’s Chatbot. Their descriptions and outbound project URLs are maintained in `index.html`.
- **Achievement:** first place in Foot Print — App Designing at the ATHENA Interschool Competition. The Instagram post is the source link; keep its linked description factual.
- **About:** a short introduction and a link on the school name to the school website.
- **Social links:** GitHub, X, Instagram, and LinkedIn links, plus a displayed Discord handle.

Check any public claim, project destination, and profile link before changing it. The Discord handle is displayed as text, not a clickable profile link.

## Notes for AI coding assistants

When modifying this repository:

1. Read the relevant section of `index.html` before editing. The page is self-contained; prefer a small change in the existing file over adding a framework or build system.
2. Preserve responsive layouts, keyboard-visible focus styles, the skip link, semantic headings, descriptive link text, and accessible names for decorative SVGs. Mark purely decorative graphics `aria-hidden="true"`.
3. Keep the dark theme and existing CSS naming patterns. Test the smallest affected viewport as well as a desktop viewport after layout changes.
4. Keep external links using `rel="noopener noreferrer"` when they open a new tab.
5. Do not invent biography details, achievements, links, or school information. Ask Taraksh when a fact or destination is uncertain.
6. Do not add a photograph or third-party analytics/tracking without explicit approval.
7. When changing public-page URLs, update the canonical URL, `og:url`, `robots.txt`, `sitemap.xml`, and this README consistently.
8. Treat Google verification tokens as secrets for configuration purposes: add only the exact public verification tag/file Google requires, never account credentials.
9. Keep the sitemap limited to public canonical pages. Do not add fragment URLs for sections of this one-page site.

## Local preview and checks

Open `index.html` in a browser for a local preview. Before publishing, check:

- The home page loads without horizontal overflow at narrow and wide viewport widths.
- Navigation anchors reach their sections.
- External links use the intended destinations.
- The school-name link opens the school website.
- `robots.txt` and `sitemap.xml` have real URLs and no `YOUR-USERNAME`, `YOUR-REPOSITORY`, or other setup placeholders.
- The deployed canonical URL, sitemap `<loc>`, `robots.txt` sitemap address, and Search Console property all refer to the same site.

