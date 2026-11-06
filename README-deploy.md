# NewU Institute blog — deploy checklist (blog.newu.institute)

Drafted Nov 6, 2026; updated Nov 6, 2026 ~16:10 ET. DRAFTS for Sean's review — nothing here is published yet.
TWO posts ready: post 1 ("What is NewU Institute?") and post 9 ("Is my coursework
private on NewU Institute?"). `index.html` already lists BOTH posts as cards.
The other 7 questions from `../blog-post-questions.md` are NOT drafted yet — draft
them one at a time after Sean confirms the list order, per the blog skill.
(The earlier version of this file said "post 1 only" — stale; Q9 was added 17:13 UTC.)
Same template style as the Top Tens blog, recolored to the NewU palette
(sky #0F94F1, navy #16263F, gray #C2C2C2 on white). Static subdomain blog,
outside the app — per the Nov 4 decision. No builder job, no app route.

## Facts used (verified Nov 6, 2026, fresh read of https://newu.institute)

- Tagline: "The Original Verifiable Alternative Post-Secondary Education Platform."
- What NewU is: free online courses (community colleges to Ivy League and
  everything in between) organized into the 100 most common majors — or a
  major you design yourself — with coursework created from course content,
  graded completion, blockchain-authenticated progress, and a Certificate of
  Post-Secondary Education any employer may freely verify at any time.
- How it works: choose a major (100 curated structures across nine fields, or
  DIY) → learn from free courses at your own pace, pausable indefinitely →
  AI-generated coursework, graded by AI with random sample re-grades to check
  the grader, admin adjusts the rubric if it drifts → progress anchored to the
  blockchain step by step, unalterable by app or admins.
- Passing bar: every piece of coursework and every course requires 70/100.
  1 in 4 finished courses gets a random spot check asking you to explain a
  piece of your own work in your own words; a short explanation goes to a
  human reviewer, and no action is ever taken without a human-reviewed
  decision.
- Pricing: $79.99 a month (pausable at any time, pick up where you left off)
  or $999 once. Course materials are only ever free online things; no tuition
  debt.
- Identity: no government ID required. Contact: newuinstitute@aol.com.
- Accreditation honesty (Sean's standing rule): NewU Institute is NOT an
  accredited university and does NOT award a degree. The post says so plainly.
  Certificate only.

## Deliberately NOT claimed in post 1

- No Certificate issuance fee, no 7-gates detail, no Merkle-root wording — all
  are spec/memory facts, not stated on the homepage read Nov 6. Add them only
  if the live site states them.
- No Terms/Privacy URLs — the homepage links to Google Sites pages but the
  exact NewU URLs were not captured in the Nov 6 read. The post links to
  newu.institute and the contact email instead.

## Deploy steps (Sean, GitHub web + Cloudflare — app untouched)

Same pattern as the Top Tens blog (blog.toptens.best, live Nov 5):

1. Create a NEW GitHub repo for the blog (e.g. `newu-blog`), public.
2. Upload these files to the repo root via GitHub web (Add file / Upload files):
   `index.html` + `what-is-newu-institute.html` + `is-my-coursework-private-on-newu-institute.html`.
   Q9's own header still carries a "DO NOT PUBLISH YET" hold — its condition was
   "publish only after the Workers AI + Serper deploy is live." That condition is
   now met: the Serper build f1d7dc27 went live at 100% traffic ~13:20 ET Nov 6,
   and the follow-up build 30608de8 is live at 100% traffic since ~14:00 ET Nov 6
   (both include Workers AI + Serper). Remove that hold comment from the Q9 file
   before uploading, or leave it — it is an HTML comment, invisible to readers.
   One open item, not a blocker: whether blockchain anchoring is actually live in
   the current build is still unverified — but the same claim already stands on
   the live homepage and in the live privacy policy Sean approved, so the blog
   saying it matches what NewU already publishes.
3. In the new repo: Settings → Pages → Build and deployment, source "Deploy
   from a branch", branch main, folder / (root). Set Custom domain to
   `blog.newu.institute` and save. (GitHub will create the CNAME file.)
4. In Cloudflare (newu.institute DNS): add ONE record — Type CNAME, Name
   `blog`, Target `notooall63.github.io`, Proxy status DNS only (grey cloud,
   NOT proxied) until GitHub issues the certificate. Adding this record does
   not touch existing newu.institute records or the Worker.
5. Once the certificate is issued, tick Enforce HTTPS in the repo's Pages
   settings. Then verify live: https://blog.newu.institute/ and the post URL.
6. Link the blog from newu.institute when ready (optional — the blog links
   back to newu.institute on every page).

## Files

- index.html — blog home (2 cards: post 1 + post 9)
- what-is-newu-institute.html — post 1: "What is NewU Institute?"
- is-my-coursework-private-on-newu-institute.html — post 9: "Is my coursework private on NewU Institute?" (hold condition met — see step 2)

## Remaining (not drafted)

2. What is a verifiable credential?
3. Can I get a degree without going to college?
4. Is NewU Institute accredited?
5. How does NewU verify coursework?
6. How much does NewU cost?
7. What is a DIY major?
8. Do employers accept NewU credentials?
