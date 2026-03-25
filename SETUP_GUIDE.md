# 🚀 FREE WILL AI — SETUP GUIDE
## Deploy from Your Android Phone in Under 1 Hour

---

## WHAT YOU'RE DEPLOYING
A complete SaaS platform with:
- Landing page + 6 app pages
- Real Stripe payments (subscriptions + one-time)
- PayPal + Google Pay via Stripe
- Claude AI script generator
- Supabase user auth + database
- Netlify serverless backend

---

## STEP 1: CREATE YOUR 3 FREE ACCOUNTS (30 min)

### A) Stripe (payments)
1. Go to stripe.com → Create account
2. Go to Developers → API Keys
3. Copy your **Publishable Key** (starts with pk_test_)
4. Copy your **Secret Key** (starts with sk_test_)
5. Go to Products → Add Product:
   - "Starter" → $49/month recurring → Copy Price ID (price_xxx)
   - "Pro" → $149/month recurring → Copy Price ID
   - "Empire" → $499/month recurring → Copy Price ID
   - "Script Templates" → $29 one-time → Copy Price ID
   - "Setup Guide" → $19 one-time → Copy Price ID
6. Go to Developers → Webhooks → Add Endpoint:
   - URL: https://YOUR-SITE.netlify.app/.netlify/functions/stripe-webhook
   - Events: checkout.session.completed, customer.subscription.deleted, invoice.payment_failed
   - Copy **Webhook Signing Secret** (starts with whsec_)

### B) Supabase (database + auth)
1. Go to supabase.com → New Project → Name it "freewillai"
2. Go to Settings → API
3. Copy your **Project URL** (https://xxx.supabase.co)
4. Copy your **anon/public key** (starts with eyJ)
5. Copy your **service_role key** (starts with eyJ — keep this secret)
6. Go to Table Editor → Create these tables:
   - Table: `users` — columns: id, email, plan, stripe_customer_id, created_at
   - Table: `campaigns` — columns: id, user_id, name, niche, voice, frequency, monetization, status, created_at
   - Table: `scripts` — columns: id, user_id, campaign_id, hook, body, cta, platform, created_at
7. Go to Authentication → Providers → Enable Email (magic links)

### C) Anthropic (AI)
1. Go to console.anthropic.com → Create account
2. Go to API Keys → Create Key → Name it "freewillai-prod"
3. Copy the key immediately (starts with sk-ant-) — you can only see it once!

---

## STEP 2: DEPLOY TO NETLIFY (10 min)

1. Go to netlify.com → Log in or create free account
2. Tap "Add new site" → "Deploy manually"
3. Zip the entire freewillai folder on your phone
4. Upload the zip to Netlify
5. Your site goes live at a random URL (you can rename it)

---

## STEP 3: ADD YOUR SECRET KEYS TO NETLIFY (10 min)

Go to: Site Configuration → Environment Variables → Add Variable

Add each of these one at a time:

| Key Name | Value | Where to find it |
|----------|-------|-----------------|
| STRIPE_SECRET_KEY | sk_test_xxx | Stripe → Developers → API Keys |
| STRIPE_PUBLISHABLE_KEY | pk_test_xxx | Stripe → Developers → API Keys |
| STRIPE_WEBHOOK_SECRET | whsec_xxx | Stripe → Developers → Webhooks |
| STRIPE_PRICE_STARTER | price_xxx | Stripe → Products → Starter |
| STRIPE_PRICE_PRO | price_xxx | Stripe → Products → Pro |
| STRIPE_PRICE_EMPIRE | price_xxx | Stripe → Products → Empire |
| STRIPE_PRICE_SCRIPTS | price_xxx | Stripe → Products → Script Templates |
| STRIPE_PRICE_GUIDE | price_xxx | Stripe → Products → Setup Guide |
| SUPABASE_URL | https://xxx.supabase.co | Supabase → Settings → API |
| SUPABASE_ANON_KEY | eyJxxx | Supabase → Settings → API |
| SUPABASE_SERVICE_KEY | eyJxxx | Supabase → Settings → API |
| ANTHROPIC_API_KEY | sk-ant-xxx | console.anthropic.com → API Keys |

After adding all keys → Trigger a new deploy.

---

## STEP 4: TEST EVERYTHING (5 min)

1. Visit your site — landing page should load
2. Click "Start Free Trial" → Stripe checkout should open
3. Use test card: **4242 4242 4242 4242** — any future date, any CVV
4. You should land on success.html after payment
5. Check Stripe dashboard — you should see the test payment
6. Go to generate.html — type a topic — click Generate
7. Script should appear in 5-10 seconds

---

## STEP 5: GO LIVE WITH REAL PAYMENTS

When you're ready to charge real money:
1. In Stripe, toggle from Test Mode to Live Mode
2. Get your new LIVE keys (sk_live_xxx and pk_live_xxx)
3. Go back to Netlify Environment Variables
4. Update STRIPE_SECRET_KEY and STRIPE_PUBLISHABLE_KEY to live versions
5. Create a new live webhook endpoint in Stripe with your same URL
6. Update STRIPE_WEBHOOK_SECRET to the new live webhook secret
7. Create your live products in Stripe (same as test, just in live mode)
8. Update all STRIPE_PRICE_xxx variables to the live price IDs
9. Trigger a new Netlify deploy
10. 💰 You're live and charging real money

---

## CUSTOM DOMAIN (Optional but recommended)

1. Buy freewillai.com at namecheap.com (~$12/year)
2. In Netlify → Domain Management → Add custom domain
3. Follow the DNS instructions Netlify shows you
4. SSL certificate is automatic and free

---

## NEED HELP?

Email: michael@freewillai.com

---

*Free Will AI — Built by Michael Meier Jr. from Savannah, Georgia.*
*Built on a phone. Built for everyone.*
