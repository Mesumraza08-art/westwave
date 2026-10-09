# West Wave Immigration redesign: migration and verification checklist

Preview build, October 8, 2026. Open `index.html` in any browser (double-click works). All routes use `#/slug/` links in the preview and map 1:1 to the live URLs (e.g. `#/federal-skilled-worker/` = `/federal-skilled-worker/`), so no redirects are needed when this moves to WordPress or React.

## Verify before publishing (client must confirm)

1. **Phone number.** Three different numbers appear on the current site: +1-866-667-1377 (header and About page), +1 (437) 435-0259 (footer), +1 (647) 954-5460 (Contact page). The preview shows all three on Contact and the toll-free in the footer. Pick one and update `PHONES` in the script.
2. **Consultant credentials.** Both Neha and Minhal are listed as "RCIC Agent". Confirm each on the CICC public register and add licence numbers (CICC rules expect them in advertising). "Broker of Record" was removed from Neha's title until confirmed. Neha's employer name corrected to "Royal LePage Terrequity" (site had a typo).
3. **Regulator wording.** Old About page said the team is "regulated by the IRCC and CICC". Consultants are regulated by CICC, not IRCC. Rewritten as "trained in immigration, refugee and citizenship law".
4. **"Downtown Toronto."** The office (100 Dynamic Drive, M1V) is in Scarborough. Copy now says "in Toronto".
5. **Worldwide offices.** Old About page claims "offices and agents worldwide". Softened to "work with clients worldwide" until confirmed.
6. **Start-up Visa status.** Business page states IRCC stopped new Start-up Visa PR applications after Dec 31, 2025 and announced a 2026 entrepreneur pilot. Re-check IRCC before launch.
7. **Study permit work hours.** Page refers to "the weekly limit set by IRCC" rather than a number. Add the current figure if you want it shown.
8. **Booking embed.** The CaseCloud calendar cannot be iframed inside the preview, so Book Now uses a prominent external button. On the live site, test embedding `https://app.casecloud.ca/calendar?event=default&siteId=CCP20253483`; fall back to the button if blocked.

## Removed or corrected from the old site (do not re-add without evidence)

- Unverified stats on Work, Business and Visitor pages: "15+ years", "1490+ happy clients", "850+ new customers".
- Guarantee language: "guaranteed success", "100% success rate", "100% Yes", "100% Accurate". These conflict with the site's own Terms (no guarantee of outcomes) and with CICC advertising rules.
- Footer line "providing consultancy services for many countries since decades".
- About page skill bars (all showed 0%).
- Lorem ipsum CTA text on Business and Visitor pages; generic travel-insurance filler answers on Work, Business, Visitor pages; references to the US, UK and Australia.
- FSW proof-of-funds table (2022 figures, now outdated) replaced with a pointer to IRCC's current table.
- FSW occupation list (NOC 2016 skill types 0/A/B, retired) replaced with NOC 2021 TEER 0 to 3 rule.
- Family page said sponsors "must be a Canadian citizen". Corrected to citizen, permanent resident, or registered under the Indian Act.
- Family page table labelled "Requirements from Quebec" was actually a LICO income table with old figures. Removed; Quebec note added.
- Family page "success rate... extensive portfolio of satisfied clients" claim removed.
- FSW "1 year in last 10" now states 1,560 hours and TEER 0 to 3; language now CLB 7 in all four abilities; tests list now includes TEF/TCF.

## Content migrated

- Home: hero message, About Us, Why We Started, Our Ethics, consultants intro, 4 destinations (original copy), 7 reasons (original list), service summaries.
- About: company intro, 6 "why choose us" items, Ethics, both team bios and photos.
- Services: FSW, PNP, Study Permit, Family Sponsorship, Work Permit, Business, Visitor Visa (visitor page existed but was missing from the old menu).
- Blog: all 184 published articles with original dates, featured images and full body text. Internal links rewritten to the new routes. Em dashes in article text replaced with commas per house style.
- Contact: address, both emails, open hours (Mon to Fri 9 to 6), Google Maps link.
- Privacy & Legal: all five policies verbatim (Privacy, Terms, Cookies, Disclaimer, AODA).
- Thank-you page kept for the booking confirmation flow.

## New in the redesign

Airplane page transitions (0.95s, reduced-motion fallback, back/forward supported), first-visit logo intro (skippable, once per browser), Pathway Finder (labelled informational only), filterable service directory, destination explorer with airport codes, journey timeline, consultation drawer, sticky consultation button, blog search + topic filters + pagination, article reading progress, full-screen mobile menu, FAQ accordions, per-page titles, descriptions, canonicals and JSON-LD (ProfessionalService, BreadcrumbList, FAQPage, BlogPosting).

## Contact form integration plan

The preview form validates every field but deliberately does not claim to send. To go live, post the form to the LeadConnector/GoHighLevel form already used on the current Contact page (`inline-uYpZLKVwrp1lBIYmFklQ`), or to a WordPress endpoint (Contact Form 7 / WPForms REST) that emails info@westwaveimmigration.com. Show the success state only after a 200 response.

## SEO launch notes

- Keep every existing slug (already matched). Add `/immigration-services/` and `/pathway-finder/` to the sitemap.
- In production, serve real paths (not `#/`) with server-side rendered titles and meta, or build each page as a WordPress page so crawlers see content without JavaScript.
- Submit the new sitemap in Search Console; robots.txt should allow all and point to `/sitemap_index.xml`.
- 11 blog posts are in "Uncategorized" and topics are messy (82 posts in "Immigrants"). The preview assigns topics from titles; tidy WordPress categories to match.

## Tested

All 18 routes at 1440px and 390px: correct H1, unique title, no script errors, no horizontal scroll. Transitions, mobile menu, drawer, finder, blog search and form validation exercised.

## Version 2 (botanical redesign), October 8, 2026

- New design system: ivory and cream base, sage and olive greens, coral reserved for CTAs, the plane and the transition curtain. Instrument Serif headlines, DM Sans body, DM Mono labels. Single light theme by design.
- Artwork built for this site: three monstera leaf illustrations (vector, generated with real split and hole geometry), a top-down airliner, and four city skylines (CN Tower, Chateau Frontenac, Canada Place sails with the North Shore mountains, Peace Tower).
- Logo intro uses the real logo: the leaf icon and each wordmark letter are cut directly from the original PNG, not redrawn. Plays once per browser session, skippable.
- Page transition: the plane enters from the left and tows a coral curtain across the screen, the page swaps while covered, and the curtain slides off to the right (about 0.95s). Reduced-motion users get a short fade.
- Primary buttons use a slightly deeper coral (#D92D2D) than the brand #F53A3A so white button text meets WCAG AA contrast.
- The reference images mentioned in the brief did not arrive with the upload; colours follow the hex codes given in the brief. Send the images if the greens or the plane style should match them more closely.
- Tested: all 18 routes at 1440px and 390px (no script errors, no horizontal scroll), intro and transition frames reviewed. Not tested at 1024, 768 or 320px.

## Version 3, October 9, 2026

- Fixed the Insights page: article cards below the first row were fading to invisible as you scrolled (two reveal animations collided), and pagination now returns to the top of the list.
- Removed the "Skip intro" button. The intro still plays once per browser session and lasts about 3 seconds.
- Plane window on the homepage now cycles real photos of Toronto (CN Tower), Quebec City (Chateau Frontenac), Vancouver (Canada Place) and Ottawa, taken from the current site's own destination images. Note: the Ottawa photo shows the Supreme Court of Canada building, not Parliament Hill.
- Added 11 themed illustrations (generated in Higgsfield with Recraft V4.1 in the site palette): six pathway panels, a travel flat-lay (home About), a Canadian lake panorama (Why Canada), documents (services column and About page), a compass (Pathway Finder), a consultation table (Booking) and a map (Contact). Each service page also shows its pathway illustration beside the overview.
- New plant types drawn as vector art alongside the monstera: palm frond, fern, silver-dollar eucalyptus, banana leaf and olive branch, spread across pages so each page mixes different plants.
