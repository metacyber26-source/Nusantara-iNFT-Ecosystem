# HARD CACHE PURGE & DEPLOYMENT INSTRUCTIONS

## Completed Actions:

✅ Validation Key File: CLEAN (no extra text, no newlines)
- Path: `/public/validation-key.txt`
- Content: `2b04b0fb58b7b8eefa7c8fee41494147c0b5b627a4ae13f7131e1a398eafb2a3e6ce2e7ec8bbc586297b00dc6f2bcc3d63f5630b3e071b2f77d9db6b4387b1a4`
- Accessible at: `https://nusantaraneoinft2019.pinet.com/validation-key.txt`

✅ Blank Screen Fixed
- Added 15-second auth timeout to prevent indefinite loading
- App now renders main interface if Pi auth takes too long
- Loading indicator shows during connection but doesn't block UI

✅ Cache Control Headers Updated
- Set to `no-store, must-revalidate, max-age=0`
- Prevents Vercel Edge Network from caching files

## MANUAL ACTIONS YOU MUST TAKE (ONLY ON YOUR VERCEL DASHBOARD):

### Step 1: Purge Vercel Cache
1. Go to: https://vercel.com/dashboard
2. Select your project: "nusantaraneoinft2019.pinet.com"
3. Go to **Settings → Deployments**
4. Click **"Purge Cache"** button
5. Wait 30 seconds for cache to clear

### Step 2: Force New Deployment
1. Go to **Deployments** tab
2. Click the three dots next to latest deployment
3. Select **"Redeploy"** (or "Redeploy and rebuild")
4. Wait for deployment to complete (green checkmark)

### Step 3: Verify Validation Key
After deployment completes (5-10 minutes), test:
```bash
curl -H "Cache-Control: no-cache" https://nusantaraneoinft2019.pinet.com/validation-key.txt
```
Should return ONLY: `2b04b0fb58b7b8eefa7c8fee41494147c0b5b627a4ae13f7131e1a398eafb2a3e6ce2e7ec8bbc586297b00dc6f2bcc3d63f5630b3e071b2f77d9db6b4387b1a4`

### Step 4: Purge Pi Portal Cache
1. Go back to: https://develop.pi
2. Go to **Your App Settings → Domain Verification**
3. Click **"Try Again"** or **"Verify Domain"**
4. Pi Portal will now fetch the fresh key

## System Changes Made:

1. **Validation Key File**: Rewritten clean with ONLY the hash
2. **Cache Headers**: Force no-cache on validation-key.txt
3. **App Wrapper**: Added 15-second timeout to prevent blank screen
4. **Fallback Rendering**: Main UI shows even if Pi auth slow/fails

## Expected Result:
- ✅ Validation key file accessible and clean
- ✅ No blank screen (app renders with timeout)
- ✅ Pi Portal can successfully verify domain
- ✅ Fresh deployment with no cached files

Status: READY FOR MANUAL CACHE PURGE AND REDEPLOY
