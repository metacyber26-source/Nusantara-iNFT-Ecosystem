# EXACT CONFIGURATION FOR Pi DEVELOPER PORTAL
## Step 10 Checklist - Copy & Paste Ready

---

## APPLICATION URL (Required)

### Location in Portal
```
Develop > Applications > [Your App] > Settings > Application URLs
```

### Exact URL to Configure
```
https://nusantara-neo.vercel.app
```

**Do NOT use:**
- ❌ `http://` (must be HTTPS)
- ❌ `localhost:3000` (production only)
- ❌ Trailing slash `https://nusantara-neo.vercel.app/`

**Correct:**
- ✅ `https://nusantara-neo.vercel.app` (exactly as shown)

---

## PAYMENT WEBHOOK URL (Required)

### Location in Portal
```
Develop > Applications > [Your App] > Webhooks > Payment Events
```

### Exact URL to Configure
```
https://nusantara-neo.vercel.app/api/webhooks/pi-payment
```

### Event Type
```
payment.completed
```

### Method
```
POST
```

**Do NOT use:**
- ❌ `http://` (must be HTTPS)
- ❌ `/api/webhook/` (missing 's')
- ❌ Trailing slash `/api/webhooks/pi-payment/`

**Correct:**
- ✅ `https://nusantara-neo.vercel.app/api/webhooks/pi-payment` (exactly as shown)

---

## ENVIRONMENT VARIABLES (Vercel Settings)

### Location
```
Settings > Environment Variables
```

### Add These Variables

```env
# Application Configuration
NEXT_PUBLIC_PI_ENVIRONMENT=mainnet
NEXT_PUBLIC_APP_URL=https://nusantara-neo.vercel.app
NEXT_PUBLIC_WEBHOOK_URL=https://nusantara-neo.vercel.app/api/webhooks/pi-payment

# From Pi Developer Portal (get from Portal Settings)
PI_PAYMENT_API_KEY=<copy from Portal>
PI_PAYMENT_WEBHOOK_SECRET=<copy from Portal>
```

### Where to Get These
1. Go to: `develop.pi`
2. Develop > Applications > [Your App] > Settings
3. Find: "API Key" → copy to `PI_PAYMENT_API_KEY`
4. Find: "Webhook Secret" → copy to `PI_PAYMENT_WEBHOOK_SECRET`

---

## PRODUCTS TO REGISTER

All 5 products must be registered in Portal:

### Main Gate (1.0 Pi)
```
Product ID: 6a2a049447f1cd1b7ccb7e68
Name: 3D Marketplace Access
Price: 1.0 Pi
```

### Secondary Products (0.5 Pi each)
```
Product ID: 6a2a05c365ccf1a5ddd44e70
Name: Batch Minting Engine
Price: 0.5 Pi
```

```
Product ID: 6a2abc564ace6de51a2b3a3a
Name: 3D Asset Marketplace
Price: 0.5 Pi
```

```
Product ID: 6a2ad9356fca3e500004295b
Name: iNFT Forge Studio Pro
Price: 0.5 Pi
```

### Premium Product (0.6 Pi)
```
Product ID: 6a2ad947bd32f55fefb40d90
Name: NFT Content Marketplace
Price: 0.6 Pi
```

---

## QUICK SETUP CHECKLIST

### In Pi Developer Portal (develop.pi)

- [ ] Log in with Pi Pioneer account
- [ ] Select your app: "Nusantara Neo iNFT Forge"
- [ ] Go to: Settings > Application URLs
  - [ ] Set: `https://nusantara-neo.vercel.app`
  - [ ] Click: Save
- [ ] Go to: Webhooks > Payment Events
  - [ ] Add new webhook
  - [ ] Event: `payment.completed`
  - [ ] URL: `https://nusantara-neo.vercel.app/api/webhooks/pi-payment`
  - [ ] Click: Save
- [ ] Go to: API Keys & Credentials
  - [ ] Copy: API Key
  - [ ] Copy: Webhook Secret
- [ ] Go to: Products > Manage Products
  - [ ] Verify all 5 products listed
  - [ ] All have correct prices
- [ ] Go to: Payment Settings
  - [ ] Check: "Enable On-Chain Payments"
  - [ ] Check: "Enable Webhook Processing"
  - [ ] Check: "Enable Production Mode" (for mainnet)
  - [ ] Click: Save

### In Vercel (vercel.com)

- [ ] Go to: Project Settings > Environment Variables
- [ ] Add:
  ```
  NEXT_PUBLIC_PI_ENVIRONMENT=mainnet
  NEXT_PUBLIC_APP_URL=https://nusantara-neo.vercel.app
  NEXT_PUBLIC_WEBHOOK_URL=https://nusantara-neo.vercel.app/api/webhooks/pi-payment
  PI_PAYMENT_API_KEY=<paste from Portal>
  PI_PAYMENT_WEBHOOK_SECRET=<paste from Portal>
  ```
- [ ] Click: Save
- [ ] Deployment: Auto-redeploys with new environment

### Testing

- [ ] Wait 1-2 minutes for Vercel deployment
- [ ] Clear browser cache (Ctrl+Shift+Del)
- [ ] Open in Pi Browser: `https://nusantara-neo.vercel.app`
- [ ] Should NOT see orange warning icon
- [ ] Should see loading spinner (not blank)
- [ ] After 5-10 seconds: payment gate appears
- [ ] Click: "Unlock for 1 Pi"
- [ ] Complete payment
- [ ] Should redirect to dashboard (not blank screen)

---

## TROUBLESHOOTING

### Problem: Still seeing white blank screen

**Solution:**
1. Check: Pi Developer Portal has application URL configured
2. Check: Browser console for errors (F12)
3. Check: Vercel deployment completed (not still building)
4. Try: Hard refresh (Ctrl+F5 or Cmd+Shift+R)
5. Try: Clear cache (Ctrl+Shift+Del)

### Problem: Orange warning icon in Pi Browser

**Solution:**
1. Verify: Application URL is `https://nusantara-neo.vercel.app`
2. Verify: URL doesn't have trailing slash
3. Verify: Portal shows "✓ Verified" next to URL
4. Try: Hard refresh

### Problem: "Product not found" error

**Solution:**
1. Check: Product ID `6a2a049447f1cd1b7ccb7e68` exists in Portal
2. Check: Product is listed in "Products" section
3. Check: Product price matches (1.0 Pi)
4. Check: Vercel deployed successfully
5. Try: Clear cache and reload

### Problem: Webhook not receiving callbacks

**Solution:**
1. Check: Webhook URL is exactly `https://nusantara-neo.vercel.app/api/webhooks/pi-payment`
2. Check: No trailing slash
3. Check: Portal shows webhook as "Active"
4. Check: Webhook secret is configured in Vercel
5. Try: Test webhook from Portal (if available)

---

## SUPPORT LINKS

- **Pi Developer Portal**: https://develop.pi
- **Pi Network Docs**: https://docs.minepi.com
- **Vercel Docs**: https://vercel.com/docs
- **This App Repo**: Check for issues/PRs

---

## FINAL VERIFICATION

After all configuration is complete:

```
✅ App URL configured in Portal
✅ Webhook URL configured in Portal  
✅ API keys added to Vercel
✅ Webhook secret added to Vercel
✅ All 5 products registered
✅ Payment processing enabled
✅ App opens without orange icon
✅ No blank screens
✅ Payment flow works end-to-end
✅ Webhook receives callbacks

= PRODUCTION READY =
```

---

## COPY-PASTE REFERENCE

### All URLs at once:
```
App: https://nusantara-neo.vercel.app
Webhook: https://nusantara-neo.vercel.app/api/webhooks/pi-payment
```

### All Product IDs at once:
```
6a2a049447f1cd1b7ccb7e68
6a2a05c365ccf1a5ddd44e70
6a2abc564ace6de51a2b3a3a
6a2ad9356fca3e500004295b
6a2ad947bd32f55fefb40d90
```

---

**Last Updated**: June 11, 2026
**Status**: Production Ready (pending Portal configuration)
