# Onboarding Payment Button - Implementation Guide

## Overview

The **Onboarding Payment Button** is the main application unlock gate for Nusantara Neo iNFT Forge. It's displayed immediately after Pi Network authentication, requiring users to complete a one-time purchase of **1.0 Pi** to unlock full access to the application.

## Architecture

### Components

1. **OnboardingPaymentButton** (`/components/onboarding-payment-button.tsx`)
   - Modal dialog that displays the unlock offer
   - Handles purchase flow and error states
   - Shows product details and features
   - Displays transaction results

2. **AppWrapper** (`/components/app-wrapper.tsx`)
   - Acts as the main application gate
   - Checks if user has purchased the main product (`PRODUCT_6a2abc564ace6de51a2b3a3a`)
   - Renders either the onboarding gate or the full app based on purchase status

### Product Configuration

Product ID: `6a2abc564ace6de51a2b3a3a`
Price: `1.0 Pi`
Name: Nusantara Neo iNFT Forge

Configured in `/lib/product-config.ts`:
```typescript
export const PRODUCT_CONFIG = {
  PRODUCT_6a2abc564ace6de51a2b3a3a: "6a2abc564ace6de51a2b3a3a",
  // ... other products
} as const;
```

## Flow

```
User Authenticates (Pi Network)
        ↓
AppWrapper checks restoredPurchases
        ↓
Has Access? → YES → Show Full App
        ↓ NO
OnboardingPaymentButton Modal Opens
        ↓
User Clicks "Unlock for 1.0 Pi"
        ↓
SDK initiates makePurchase(product.id)
        ↓
Purchase Success? → YES → Reload page (purchases auto-restore)
        ↓ NO
Show Error Message + Retry Option
```

## Usage

### For Users

1. User logs in with Pi Network
2. OnboardingPaymentButton modal appears
3. User reviews the unlock offer and features
4. User clicks "Unlock for 1.0 Pi"
5. Pi Network payment confirmation
6. On success, page reloads and user gains access

### For Developers

The payment button is automatically integrated into the app flow via `AppWrapper`. No additional setup required. The gate automatically:

- Checks purchase status on app load
- Restores previous purchases via `usePiAuth()?.restoredPurchases`
- Shows/hides the gate based on access status
- Handles all payment flow and errors

## Technical Details

### SDK Integration

Uses the Pi Network SDKLite SDK for purchase handling:

```typescript
const purchaseResult = await sdk.makePurchase(product.id)

// Success response:
{
  ok: true,
  productId: "...",
  paymentId: "...",
  txid: "..."
}

// Error codes:
- "product_not_found"
- "purchase_cancelled"
- "purchase_error"
```

### Purchase Restoration

After successful purchase, the app automatically:

1. Calls `await sdkInstance.state.restore()` to fetch restored purchases
2. Stores in `restoredPurchases` state via `usePiAuth()` hook
3. AppWrapper checks for product access and conditionally renders gate

### Hook Usage

```typescript
import { usePiAuth } from "@/contexts/pi-auth-context"

const { products, sdk, restoredPurchases, isAuthenticated } = usePiAuth()

// Check if user has access to main product
const hasAccess = restoredPurchases?.find(
  (p) => p.productId === PRODUCT_CONFIG.PRODUCT_6a2abc564ace6de51a2b3a3a
)
```

## Customization

### Modify Button Appearance

Edit `/components/onboarding-payment-button.tsx`:
- Change colors: Modify `bg-primary/15`, `text-primary` classes
- Change size: Adjust dialog `sm:max-w-md` breakpoint
- Change text: Update description and feature list

### Modify Product Details

Product details are fetched from Pi Network product catalog. To change:
1. Update the product in Pi Network admin
2. The app automatically fetches updated details

### Add Custom Callback

```typescript
<OnboardingPaymentButton 
  onSuccess={() => {
    console.log("User unlocked!")
    // Custom logic here
  }}
/>
```

## Error Handling

The component handles three error scenarios:

1. **Product Not Found**
   - Message: "Product not found. Please try again."
   - Action: User can retry the purchase

2. **Purchase Cancelled**
   - Message: "Purchase cancelled."
   - Action: User can dismiss and try again later

3. **Purchase Error**
   - Message: "Purchase failed. Please try again."
   - Action: User can retry the payment

4. **SDK Not Initialized**
   - Message: "SDK not initialized. Please refresh and try again."
   - Action: User should refresh the page

## Files Modified/Created

- ✅ `/components/onboarding-payment-button.tsx` - NEW (Payment gate component)
- ✅ `/components/app-wrapper.tsx` - MODIFIED (Added gate logic)
- ✅ `/lib/product-config.ts` - EXISTING (Product ID already configured)

## Testing Checklist

- [ ] User sees auth loading screen on first load
- [ ] After auth, onboarding modal appears
- [ ] Product details display correctly with 1.0 Pi price
- [ ] Features list is visible and readable
- [ ] "Unlock for 1.0 Pi" button is clickable
- [ ] Click triggers Pi payment confirmation
- [ ] On success, success message shows
- [ ] Transaction details display (txid, payment ID)
- [ ] Page reloads after 2 seconds
- [ ] After reload, user has access to full app
- [ ] Users with existing purchases see full app immediately
- [ ] Error messages display correctly
- [ ] "Try Again" button works for failed purchases
- [ ] "Cancel" button dismisses modal

## Future Enhancements

1. **Skip Option with Watermark**: Add option to try free tier (limited features)
2. **Trial Period**: Offer 7-day trial before payment gate
3. **Family Plan**: Bundle discount for multiple users
4. **Subscription Model**: Monthly renewal vs one-time purchase
5. **Referral Rewards**: Unlock discount by referring friends
