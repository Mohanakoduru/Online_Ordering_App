# 🌿 Harika Vegetables — WhatsApp Ordering PWA

> A bilingual (Telugu + English) vegetable shop ordering app built for real-world use.  
> Zero backend cost. Installable as a mobile app. Real-time sync across all devices.

🔗 **Live Demo:** [harika-vegetables.netlify.app](https://harika-vegetables.netlify.app/)

---


## ✨ Features

### For Customers
- 🥦 Browse **55+ vegetables** with Telugu + English names and emojis
- 🔍 Search in **Telugu or English** instantly
- 🛒 Add to cart with quantity controls
- 📍 **GPS location captured automatically** — no typing address needed
- 🚚 **Delivery charge auto-calculated** by distance (Free ≤1.5 km · ₹10/km beyond)
- 📲 Full order sent to **WhatsApp** with item list, totals, and Google Maps link
- 📱 **Installable as a mobile app** — works offline too

### For Shop Admin
- 🔐 Password-protected admin panel
- 🏪 Edit shop name, tagline, WhatsApp number, delivery note
- 📍 Set shop GPS location for delivery calculation
- 🥬 Add / edit / remove vegetables (with Telugu name auto-suggest)
- ✅ Toggle items **In Stock / Out of Stock** in one tap
- 🔄 All changes **sync to every customer's phone instantly** via Firebase

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Pure HTML5 + CSS3 + Vanilla JavaScript |
| Realtime Database | Firebase Realtime Database (free tier) |
| Order Delivery | WhatsApp API (`wa.me` deep link) |
| Location | Web Geolocation API + Haversine formula |
| App Install | PWA — Web Manifest + Service Worker |
| Hosting | Netlify (free tier) |
| Languages | Telugu 🇮🇳 + English |

**No frameworks. No build tools. No npm. Single HTML file.**

---

## 📦 How It Works

```
Customer opens link
       ↓
App loads latest data from Firebase Realtime Database
       ↓
Customer browses vegetables (Telugu + English)
       ↓
Adds items to cart → GPS location captured
       ↓
Delivery charge calculated automatically
       ↓
Order sent to shop owner via WhatsApp
       ↓
Shop owner receives: items + total + delivery + Google Maps link
```

---

## 🚀 Deploy Your Own

### Step 1 — Get the file
Download `Harika_Vegetables.html` from this repo.

### Step 2 — Set up Firebase (free, 5 minutes)
1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Create a new project
3. Go to **Build → Realtime Database → Create Database**
4. Choose **Start in test mode**
5. Copy your database URL (e.g. `https://your-project-default-rtdb.firebaseio.com`)

### Step 3 — Update the Firebase URL in the file
Open `Harika_Vegetables.html` and find this line near the top of the `<script>` section:
```javascript
const FB_DEFAULT = 'https://vegetables-default-.firebaseio.com';
```
Replace with your own Firebase URL.

### Step 4 — Deploy to Netlify
1. Go to [netlify.com](https://netlify.com) → Sign up free
2. Drag and drop the HTML file
3. Your app is live!

### Step 5 — Configure your shop
1. Open your Netlify URL
2. Tap ⚙️ → Login (default: `admin` / `1234`)
3. Set your shop name, WhatsApp number, location
4. Change your admin password
5. Done — all changes sync to every device instantly!

---

## 📱 Install as Mobile App

**Android (Chrome):**
1. Open the Netlify link in Chrome
2. Tap ⋮ menu → "Add to Home Screen"
3. Tap Add — app icon appears!

**iPhone (Safari):**
1. Open the Netlify link in Safari
2. Tap Share button → "Add to Home Screen"
3. Tap Add — app icon appears!

---

## 🗂️ Project Structure

```
Harika_Vegetables.html     ← Entire app (single file)
├── <style>                ← All CSS styling
├── HTML structure         ← Product grid, modals, admin panel
└── <script>
    ├── MASTER database    ← 55+ vegetables (Telugu + English)
    ├── Firebase helpers   ← fbRead(), fbWrite(), syncToFirebase()
    ├── Product rendering  ← renderProds(), filterProds()
    ├── Cart & Checkout    ← openCart(), showCheckoutForm()
    ├── GPS & Distance     ← haversine(), delivCharge()
    ├── WhatsApp order     ← sendOrder()
    ├── Admin panel        ← saveShop(), saveLoc(), saveSecurity()
    └── PWA setup          ← setupPWA(), service worker
```

---

## 💡 Design Decisions

**Why single HTML file?**  
The shop owner needed something he could upload to Netlify with a simple drag-and-drop. No build process, no dependencies, no confusion.

**Why bilingual (Telugu + English)?**  
The admin (shop owner's father) cannot read English. Every interface element is in both languages. Telugu names auto-fill when searching, so he never needs to type them manually.

**Why Firebase Realtime Database?**  
`localStorage` only saves data on one browser. When the admin changes a price on his laptop, customers on their phones should see it immediately — Firebase makes this happen for free.

**Why WhatsApp instead of a payment gateway?**  
For a local vegetable shop in a small town, the order flow is: customer orders → shop owner calls back to confirm → cash on delivery. WhatsApp is already the communication tool everyone uses.

---

## 🔧 Customisation

You can easily customise:
- **Add more vegetables** → Admin panel → Products tab → Add Custom Item
- **Change prices** → Admin panel → tap ✏️ next to any product
- **Change delivery charge formula** → Find `delivCharge()` in the script
- **Change free delivery distance** → Edit `km<=1.5` in `delivCharge()`
- **Add your own language** → Duplicate the `te` fields in MASTER array

---

## 📄 License

MIT License — free to use, modify, and deploy for your own shop.

---

## 🙏 Built For

This app was built for a real vegetable shop in Andhra Pradesh, India. The goal was to bring a simple, working digital ordering system to a small local business — with no monthly costs, no technical maintenance burden, and a UI that works for someone who has never used a smartphone app before.

---

*Built with ❤️ using plain HTML, CSS, and JavaScript. No frameworks were harmed in the making of this project.*
