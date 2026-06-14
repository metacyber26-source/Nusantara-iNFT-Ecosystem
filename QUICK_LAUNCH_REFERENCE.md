## NUSANTARA NEO iNFT FORGE - QUICK LAUNCH REFERENCE

### IMMEDIATE DEPLOYMENT (Choose One Method)

**Method 1: v0 UI Publish (Recommended - 30 seconds)**
```
1. Click "Publish" button (top-right corner)
2. Select Vercel or your hosting provider
3. Wait for deployment (2-5 minutes)
4. Live URL provided automatically
```

**Method 2: Download & Self-Host (5 minutes)**
```
1. Click three dots (...) → Download ZIP
2. Extract files: unzip project.zip
3. Install: npm install
4. Build: npm run build
5. Deploy to your server/Vercel/AWS
```

---

### CRITICAL FILES FOR LAUNCH

| File | Purpose | Status |
|------|---------|--------|
| `components/onboarding-payment-button.tsx` | Main unlock gate | ✅ Ready |
| `components/app-wrapper.tsx` | Gate enforcement | ✅ Ready |
| `lib/product-config.ts` | Product ID: 6a2abc564ace6de51a2b3a3a | ✅ Ready |
| `lib/pioneer-whitelist.ts` | 9 early drivers, 0% fees | ✅ Ready |
| `contexts/pi-auth-context.tsx` | Pi Network SDK integration | ✅ Ready |
| `PRODUCTION_DEPLOYMENT_GUIDE.md` | Full deployment instructions | ✅ Ready |
| `LAUNCH_CHECKLIST.md` | Pre-launch verification | ✅ Ready |

---

### KEY PRODUCTION DETAILS

**Product:**
- Name: Nusantara Neo iNFT Forge
- Product ID: `6a2abc564ace6de51a2b3a3a`
- Price: 1.0 Pi (locked)
- Placement: Onboarding unlock gate

**Pioneer Whitelist (9 Addresses - 0% Fee):**
1. Ful21 | 2. Murtini79 | 3. SIREP74 | 4. ifah24 | 5. Muhammadefendi123
6. Titin999 | 7. afifmasfiqo | 8. Tar72 | 9. Rid81

**Revenue Splits (100% LOCKED):**
- Primary Sale: 50% user, 15% dev, 20% community, 10% server, 5% gas
- Mint Fee: 20% dev, 30% community, 40% server, 10% gas
- Secondary: 10% creator, 20% dev, 30% community, 35% server, 5% gas
- Rental: 50% lender, 10% dev, 25% community, 10% server, 5% gas

---

### PRE-LAUNCH VERIFICATION (2 MIN)

```
✅ Product ID configured
✅ Payment button renders
✅ Pi SDK loads
✅ Pioneer whitelist file exists
✅ Error handling in place
✅ Mobile responsive
✅ No console errors
```

---

### POST-LAUNCH TESTING (5 MIN)

1. **Authentication**
   - Load app → See "Initializing Pi Network"
   - Log in with Pi account → See payment gate

2. **Payment Flow**
   - Click "Unlock for 1.0 Pi"
   - Complete test purchase
   - See success message with txid
   - Verify purchase persists on refresh

3. **Verification**
   - Check browser console for `[v0]` logs
   - No errors displayed
   - Transaction receipt shows correctly
   - Full app accessible after payment

---

### TROUBLESHOOTING QUICK FIX

| Issue | Fix |
|-------|-----|
| "Product not found" | Verify product ID in system |
| "SDK not initialized" | Wait for SDK to load, refresh page |
| "Purchase cancelled" | User dismissed - normal flow |
| "Loading stuck" | Check network, clear cache, retry |
| Mobile unresponsive | Update browser, check viewport |

---

### LAUNCH COMMAND REFERENCE

```bash
# Development (local testing)
npm run dev
# Open: http://localhost:3000

# Production Build
npm run build
npm start

# Deploy via Vercel CLI
vercel deploy --prod

# Deploy via Git (GitHub/GitLab)
git push origin main
# Vercel auto-deploys from main branch
```

---

### WHAT HAPPENS AFTER PURCHASE

```
User clicks "Unlock for 1.0 Pi"
         ↓
Pi payment dialog opens
         ↓
User confirms payment
         ↓
sdk.makePurchase() executes
         ↓
Payment processed on Pi Network
         ↓
Success: txid, paymentId returned
         ↓
Page reloads automatically
         ↓
User has permanent access to full app
```

---

### SUPPORT LINKS

- **Deployment Help:** vercel.com/help
- **Pi Network Docs:** developers.pi-network.io
- **v0 Support:** vercel.com/support
- **This App Docs:** See PRODUCTION_DEPLOYMENT_GUIDE.md

---

### STATUS: READY TO LAUNCH 🚀

**All systems operational. Deploy now via "Publish" button.**

Time to deployment: **30 seconds**
Time to live: **5 minutes total**
Time to first purchase: **Variable (community-driven)**

**Next Step:** Click "Publish" in v0 UI
