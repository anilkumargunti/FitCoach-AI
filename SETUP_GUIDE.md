# FitCoach AI — Complete Setup Guide
### From zero to live app with payments · Made for Hyderabad creators

---

## OVERVIEW — What You're Launching

| What | How | Cost |
|------|-----|------|
| Website | Vercel (free hosting) | ₹0 |
| Android App | Google Play Store | ₹2,100 one-time ($25) |
| iOS App | Apple App Store | ₹8,300/year ($99) |
| India Payments | Instamojo | 2% per transaction |
| Global Payments | Gumroad | 10% per transaction |

**Suggested pricing:**
- Monthly plan: ₹199/month
- Single plan: ₹99 one-time

---

## PHASE 1 — DEPLOY THE WEBSITE (Free · 30 minutes)

### Step 1: Create GitHub Account
1. Go to https://github.com → Sign up (free)
2. Click "New repository" → Name it `fitcoach-ai`
3. Set to Public → Create repository

### Step 2: Upload Your Files
In your new repo, click "Add file → Upload files"
Upload ALL 5 files:
- index.html
- manifest.json
- sw.js
- capacitor.config.json
- package.json

Also create an `icons/` folder and add at least:
- icon-192.png (192×192)
- icon-512.png (512×512)
→ Make these in Canva.com for free (use a green dumbbell/lightning bolt icon)

### Step 3: Deploy on Vercel
1. Go to https://vercel.com → Sign up with GitHub
2. Click "New Project" → Import your `fitcoach-ai` repo
3. Click "Deploy" — done in 60 seconds
4. Your live URL: https://fitcoach-ai.vercel.app

### Step 4: Custom Domain (Optional, ₹800/year)
1. Buy `fitcoachai.in` on GoDaddy or Namecheap (~₹800/year)
2. In Vercel → Settings → Domains → Add your domain
3. Follow DNS setup instructions (5 minutes)

---

## PHASE 2 — SETUP PAYMENTS (1-2 hours)

### INSTAMOJO (India — UPI, Cards, Net Banking)

**Step 1: Create Account**
1. Go to https://instamojo.com → Sign Up
2. Choose "Sell Online" as your use case

**Step 2: Complete KYC (Required for payouts)**
You'll need:
- Aadhaar card number
- PAN card number
- Bank account details (for receiving money)
- KYC usually approved in 2-4 hours

**Step 3: Create Payment Links**

For Monthly Plan (₹199):
- Dashboard → Payment Links → Create Payment Link
- Title: "FitCoach AI — Monthly Subscription"
- Amount: ₹199
- Description: "Unlimited AI fitness plans + daily calorie tracker. 30 days access."
- Redirect URL: https://fitcoachai.in/?paid=true (your Vercel URL)
- Copy the link (looks like: imojo.in/fitcoachmonthly)

For Single Plan (₹99):
- Same steps, amount: ₹99
- Redirect URL: https://fitcoachai.in/?paid=true

**Step 4: Add Links to App**
Open index.html, find these two lines:
```
href="YOUR_INSTAMOJO_LINK"  (for monthly, line ~290)
```
Replace with your actual Instamojo links.

**Step 5: Payouts**
- Money goes to your bank account automatically
- Payout happens every 3 business days
- Minimum payout: ₹100

---

### GUMROAD (International — Credit/Debit Cards)

**Step 1: Create Account**
1. Go to https://gumroad.com → Create Account
2. Connect PayPal (for receiving international payments)
   → If no PayPal: create one at paypal.com (free, works in India)

**Step 2: Create Product**
- Products → New Product → Digital Product
- Name: "FitCoach AI — Monthly Plan"
- Price: $3.99 (or ₹199 equivalent)
- Description: "AI-powered workout & meal plans + calorie tracker"
- Content: Type "Access: https://fitcoachai.in/?paid=true"
- Publish

**Step 3: Copy Product URL**
Copy your Gumroad product URL (e.g., fitcoach.gumroad.com/l/fitcoach)
Add it to index.html where it says YOUR_GUMROAD_LINK

**Payouts:** Gumroad pays via PayPal on Fridays.
PayPal → Indian bank transfer takes 3-5 business days.

---

### REMOVE DEMO BUTTON (Before Launch!)
In index.html, find and DELETE this entire block:
```html
<button class="demo-skip" onclick="goTo('app')">🔧 Demo — Skip Payment...</button>
```

---

## PHASE 3 — ANDROID APP (Google Play · ₹2,100 one-time)

### What you need:
- A Windows PC or Mac
- Android Studio (free): https://developer.android.com/studio
- Node.js (free): https://nodejs.org

### Step 1: Install Tools
```bash
# Install Node.js first, then:
npm install -g @capacitor/cli
npm install
npx cap add android
```

### Step 2: Build Android App
```bash
npx cap sync android
npx cap open android
```
→ Android Studio opens. Wait for it to load.

### Step 3: Generate Signed APK
In Android Studio:
1. Build → Generate Signed Bundle/APK
2. Choose "Android App Bundle (.aab)"
3. Create a new keystore (save this file safely — you need it forever!)
   - Key alias: fitcoachai
   - Password: (create a strong one, save it!)
4. Build → Release AAB file is created

### Step 4: Google Play Console
1. Go to https://play.google.com/console → Pay $25 one-time
2. Create app → "FitCoach AI"
3. Fill in:
   - App description (copy from your landing page)
   - Category: "Health & Fitness"
   - Screenshots (take 4-5 phone screenshots of the app)
   - Icon: your 512×512 icon
4. Upload the .aab file you built
5. Submit for review → takes 3-7 days

**Total Android cost: $25 one-time (~₹2,100)**

---

## PHASE 4 — iOS APP (Apple App Store · ₹8,300/year)

### What you need:
- A Mac computer (mandatory — cannot build iOS on Windows)
- Xcode (free from Mac App Store)
- Apple Developer account: $99/year at developer.apple.com

### Step 1: Setup
```bash
npm install
npx cap add ios
npx cap sync ios
npx cap open ios
```
→ Xcode opens automatically

### Step 2: Configure in Xcode
1. Click on "App" in the left panel
2. Bundle Identifier: in.fitcoachai.app
3. Team: Select your Apple Developer account
4. Signing Certificate: Automatic

### Step 3: Archive & Upload
1. Product → Archive
2. Distribute App → App Store Connect → Upload
3. Go to https://appstoreconnect.apple.com
4. Fill in app details, screenshots, description
5. Submit for review → takes 1-3 days

**Recommendation:** Launch Android first (cheaper, faster review).
Add iOS once you're making consistent revenue.

---

## PHASE 5 — PROMOTE & EARN (Free Channels)

### Week 1 — Hyderabad Focus
- Post in WhatsApp fitness groups in Hyderabad
- Share in Telegram fitness channels (search "Hyderabad fitness")
- Post on your personal Instagram with a demo video

### Week 2 — Scale Online
- Reddit: r/india, r/hyderabad, r/fitness, r/indianfitness
- Facebook: Search "Hyderabad Gym" groups — there are 50+ with 10k+ members
- Quora: Answer fitness questions, mention your app

### The Best Growth Hack — Instagram Reel
Record a 30-second screen recording:
"I built an AI fitness coach that gives you a custom workout + tracks your calories for just ₹199/month"
Show: form → AI generating plan → calorie tracker
This kind of content regularly goes viral in Indian fitness communities.

---

## REVENUE PROJECTIONS

| Daily Sales | Monthly Revenue |
|-------------|----------------|
| 2 (₹199 each) | ₹11,940 |
| 5 | ₹29,850 |
| 10 | ₹59,700 |
| 20 | ₹1,19,400 |

After Instamojo 2% fees.

---

## TIMELINE SUMMARY

| Day | Task |
|-----|------|
| Day 1 | Deploy website on Vercel (free) |
| Day 2 | Set up Instamojo KYC + payment links |
| Day 3 | Add payment links to app, remove demo button, go live |
| Day 4-5 | Start promoting in WhatsApp/Telegram groups |
| Week 2 | Post Instagram Reel, Reddit posts |
| Month 2 | If making ₹5,000+/month, pay ₹2,100 for Google Play |
| Month 4 | If making ₹15,000+/month, pay ₹8,300 for Apple App Store |

---

## SUPPORT

Stuck on any step? Go to claude.ai and ask for help.
Every step above can be guided by Claude for free.

Good luck from Hyderabad to the world! 🇮🇳💪
