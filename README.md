# Duke Yoga - v2 redesign

Bold editorial redesign: static site, no platform lock-in, no frameworks, no build step. Edit any `.html` file in a text editor and re-upload.

## What changed vs the old site (and why)

- **Structure, not just skin.** The standalone Reviews page is gone - testimonials now appear on every page where they do persuasive work, and `/reviews` 301-redirects to `/about-us#reviews` (see `_redirects`, works on Cloudflare Pages and Netlify).
- **New FAQ section on the home page** answering the objections that actually stop first-timers: "I'm not flexible", "am I too old", "what do I bring", "what does it cost".
- **Interactive breathing guide** on the home page - a 12-second animated breath circle. On-brand, memorable, and respects `prefers-reduced-motion`.
- **Week-strip timetable** - swipeable day cards on the home page, full editorial schedule on the Classes page.
- **New palette**: warm cream + terracotta + deep plum, with the heritage purple kept as an accent. Big Fraunces display type.
- **Sticky mobile CTA** ("First class free - book now") and a persistent CTA band above the footer on every page.
- Kept from v1: same URL paths (`/yoga-classes`, `/chair-yoga`, etc.) so rankings carry over; LocalBusiness structured data; sitemap; robots.txt.

## Before launch (in order)

1. **Photos.** Export images from GoDaddy (Website Builder → Media library) *before* cancelling anything - they disappear with the subscription. Save as `images/fiona-tree-pose.jpg` (home) and `images/fiona-portrait.jpg` (about). Until then, styled placeholder shapes show; nothing breaks. The design will look dramatically better with real photos - prioritise this.
2. **Contact form.** In `contact-us.html`, replace `YOUR_EMAIL_HERE` in the form action with the email that should receive enquiries. Submit once to trigger the formsubmit.co activation email.
3. **Booking tool.** Set up Bookwhen, TeamUp or Momence with the 4 weekly classes, then paste the embed code into the marked slot in `yoga-classes.html`. Until then the page falls back to "message Fiona".
4. **Workshop card.** Update the "date to be announced" card in `yoga-workshops.html` when the next date is set.
5. **Privacy policy.** `privacy-policy.html` is a draft - review it, and update it if you add analytics or the booking tool.

## Deploying (Cloudflare Pages, free)

1. Cloudflare account → Workers & Pages → Create → Pages → Upload assets (or connect a GitHub repo for version history - recommended).
2. Upload this folder; test on the free `*.pages.dev` URL first.
3. Add custom domains `dukeyoga.co.uk` and `www.dukeyoga.co.uk`.
4. Cloudflare serves `/yoga-classes` from `yoga-classes.html` automatically - existing URLs keep working.

Netlify also works (drag-and-drop; switch the form per the comment in `contact-us.html`).

## DNS cutover (keep the domain at GoDaddy)

No domain transfer needed. GoDaddy → Domains → dukeyoga.co.uk → DNS: replace the A/CNAME records with the ones Cloudflare Pages provides. The old site stays live until DNS switches; revert the records if anything's wrong. Cancel Website Builder only **after** launch and photo export.

## After launch - the real SEO levers

- **Google Business Profile**: the biggest factor for "yoga classes near me" (12,100 UK searches/mo). Complete the profile, add photos, ask happy students for Google reviews.
- The **chair-yoga page** targets "chair yoga near me" (590/mo vs 20 for "seated yoga"). Link to it from Facebook posts.
- Submit `https://dukeyoga.co.uk/sitemap.xml` in Google Search Console.

## File map

| File | Page |
|---|---|
| index.html | Home (long-form journey: hero → breathe → styles → week → Fiona → proof → FAQ) |
| yoga-classes.html | Timetable + booking |
| chair-yoga.html | Chair/seated yoga |
| private-lessons.html | 1-to-1 sessions |
| yoga-workshops.html | Workshops |
| about-us.html | Fiona + all testimonials |
| contact-us.html | Contact form |
| privacy-policy.html | Privacy |
| css/style.css | All styling (palette in `:root` at the top) |
| _redirects | /reviews → /about-us#reviews |
