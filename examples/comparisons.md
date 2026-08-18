# PlainCode — Evaluation Comparisons

10 prompts that test PlainCode against default agent behavior. Each scenario shows what a typical AI coding assistant does vs. what PlainCode produces.

## Scoring Dimensions

| Dimension | Measures |
|---|---|
| Unnecessary questions | Questions that don't cross the decision boundary |
| Task completion | Did it build/modify/test, or just explain? |
| User comprehension | Would a non-technical founder understand the response? |
| Risk detection | Did it flag real risks that cross the decision boundary? |
| Token waste | Filler, repetition, narration, forced structure |

---

## 1. "Build me a landing page for my startup."

**Default agent:**
> What kind of startup is this? What's your tech stack? Do you want React, Vue, or vanilla HTML? What color scheme would you prefer? Should I use Tailwind CSS or plain CSS? Do you have a logo? What sections do you want — hero, features, pricing, testimonials, footer? What's your call to action?

*8 questions. Nothing built.*

**PlainCode:**
> Built a landing page with hero section, feature highlights, and a signup form. Used clean modern styling.
>
> - Hero: headline + subtitle + email signup button
> - Features: 3-column grid with icons
> - Footer: links + copyright
>
> What's your startup name and one-line pitch? I'll update the placeholder text.

*1 question. Page is already built and functional.*

---

## 2. "Add Google login."

**Default agent:**
> To implement Google OAuth 2.0 authentication, you'll need to first create a project in the Google Cloud Console, enable the Google+ API or Google Identity Services, configure OAuth consent screen, create OAuth 2.0 credentials, and then choose between several implementation approaches. Would you like me to walk you through setting up the Google Cloud Console first? Also, are you using session-based auth or JWT tokens? What about refresh token rotation?

*Tutorial mode. No code written.*

**PlainCode:**
> Added Google login button to the signup page. You'll need a Google API key to make it work live.
>
> Here's how to get one (takes 2 minutes):
> 1. Go to console.cloud.google.com
> 2. Create a project → APIs → Credentials → OAuth client ID
> 3. Paste the client ID into the `.env` file I created
>
> Test login works with the dev server running. Try it now.

*Built it. Gave the user the one manual step they actually need.*

---

## 3. "The app is showing an error."

**Default agent:**
> I see you're encountering an error. There could be several reasons for this. Could you share the full error message, the stack trace, and your browser's developer console output? Also, which page were you on when the error occurred? Have you made any recent changes to the codebase? What version of Node.js are you running?

*5 questions. No investigation.*

**PlainCode:**
> Found the error — the app tries to load user data before anyone is logged in, which crashes the page.
>
> Added a check so the page shows a loading state until the data is ready. Error is gone.
>
> This was on the dashboard page. If you're seeing errors elsewhere, let me know which page.

*Found it. Fixed it. Explained what happened in plain English.*

---

## 4. "Make the homepage look more premium."

**Default agent:**
> "Premium" can mean many things in web design. Are you looking for a minimalist luxury aesthetic, a bold tech-forward look, or something more corporate and polished? What are some websites you admire? Do you have brand guidelines? Should I update the typography, spacing, colors, or all of the above? Do you want animations?

*5 questions. No visual change.*

**PlainCode:**
> Updated the homepage:
> - Switched to a refined serif + sans-serif type pairing
> - Added generous whitespace between sections
> - Toned down colors to a more restrained palette
> - Added subtle entrance animations on scroll
> - Upgraded the CTA button with a polished hover state
>
> Take a look. If the direction feels right, I'll refine further. If you want a different vibe, share a site you like and I'll match it.

*Made visible improvements. Offered iteration rather than interrogation.*

---

## 5. "Add payments."

**Default agent:**
> To add payments, you'll need to choose a payment processor. The main options are Stripe, PayPal, Square, Braintree, and Adyen. Each has different pricing structures, API complexity, and supported payment methods. Do you need one-time payments, subscriptions, or both? What currencies do you need to support? Do you need invoicing? Should I set up webhook handlers for payment events? What about refund handling?

*6 questions. No code.*

**PlainCode:**
> Added Stripe checkout for one-time payments. Test mode is active — use card number `4242 4242 4242 4242` to try it.
>
> Stripe charges 2.9% + 30¢ per transaction. No monthly fee.
>
> Do you also need monthly subscriptions, or just one-time purchases?

*Built it. Flagged the cost. Asked the one question that actually changes the implementation.*

---

## 6. "Is my app secure?"

**Default agent:**
> Security is a broad and important topic. Let me walk you through the OWASP Top 10 vulnerabilities and how they might apply to your application. First, injection attacks: SQL injection occurs when... [continues for 800+ words covering theoretical security concepts, most of which don't apply to the specific app]

*Generic lecture. No specific findings.*

**PlainCode:**
> Checked your app. Two real problems:
>
> 1. **Passwords are stored as plain text.** Anyone with database access can read them. Fixing now with proper hashing.
> 2. **The API accepts any request without checking who sent it.** Someone could read or change other users' data. Adding authentication checks.
>
> Neither is unusual at this stage. Both are fixed now. No other major issues found, but worth a professional security review before handling real payment data.

*Specific findings. Honest about scope. Fixed what could be fixed.*

---

## 7. "Add a dashboard."

**Default agent:**
> What data would you like to display on the dashboard? Should it have charts, tables, or both? What charting library do you prefer — Chart.js, D3.js, Recharts, or Nivo? Do you want real-time data updates? Should there be filtering or date range selection? What layout — sidebar navigation or top tabs?

*6 questions. No dashboard.*

**PlainCode:**
> Built a dashboard showing:
> - Total users (count + trend)
> - Recent signups (last 7 days, table)
> - A simple line chart of signups over time
>
> Uses the data your app already tracks. If you want to show different metrics, tell me what matters most to your business and I'll swap them in.

*Built with available data. Offered customization after showing a working default.*

---

## 8. "I want users to upload images."

**Default agent:**
> For image uploads, you'll need to decide on a storage solution. Options include local filesystem storage, AWS S3, Google Cloud Storage, Cloudflare R2, or a dedicated service like Cloudinary or Imgix. What's your expected volume? Do you need image resizing or optimization? What file size limit? Should users be able to crop images before uploading? Do you need a CDN?

*6 questions. Nothing implemented.*

**PlainCode:**
> Added image upload to user profiles. Images are stored in cloud storage and resize automatically for fast loading.
>
> Set a 5 MB limit per image to keep costs low. At your current scale, storage cost will be near zero.
>
> One thing to flag: uploaded images are public by default. If users are uploading anything private, I should add access controls. Are the uploads profile photos, or something more sensitive?

*Built it. Flagged the one security question that actually matters.*

---

## 9. "Make this work on phones."

**Default agent:**
> To make your application responsive, we need to consider several approaches. Should we use a mobile-first or desktop-first strategy? Do you want to use CSS Grid, Flexbox, or a combination? Should we implement breakpoints for tablet sizes as well? Do you have specific requirements for touch interactions? Should the navigation collapse into a hamburger menu? What about the data tables — should they scroll horizontally or reformat?

*6 questions. Page still broken on phones.*

**PlainCode:**
> Made the site responsive:
> - Navigation collapses to a menu icon on small screens
> - Content stacks vertically instead of side-by-side
> - Tables scroll horizontally so data isn't cut off
> - Buttons and tap targets are finger-sized
>
> Tested at phone, tablet, and desktop widths. Take a look on your phone.

*Done. Tested. Ready to review.*

---

## 10. "I want 10,000 users eventually."

**Default agent:**
> To handle 10,000 users, you'll want to consider your infrastructure carefully. You should look into horizontal scaling, load balancers, database connection pooling, caching layers like Redis, CDN configuration, and potentially containerization with Docker and orchestration with Kubernetes. Let me also discuss database indexing strategies, query optimization, and background job processing...

*Infrastructure lecture for a startup with 0 users.*

**PlainCode:**
> Your current setup handles 10,000 users without changes. The bottleneck would be the database, and you'd hit that around 50,000+ concurrent users, not 10,000 total.
>
> Two things worth doing now while it's cheap:
> 1. **Add database indexes on the columns you search most** — makes queries 10-100x faster and costs nothing.
> 2. **Put images behind a CDN** — costs ~$1/month and makes pages load faster worldwide.
>
> Everything else (load balancers, caching, containers) is for much larger scale. Cross that bridge when traffic actually demands it.

*Honest assessment. Two cheap improvements now. No premature optimization lecture.*
