SPARK KITS CHECKOUT UPDATE

Files:
- kits.html
- kit-checkout.html
- kit-order-success.html
- STORE_RULES_ADDITIONS.txt
- STORE_STORAGE_RULES_ADDITIONS.txt

Create Firestore document:
storeSettings/main

Example:
{
  "gstEnabled": true,
  "gstRate": 18,
  "upiId": "your-upi-id",
  "qrUrl": "Firebase Storage download URL",
  "paymentTitle": "Scan the QR and pay the exact total shown below.",
  "paymentInstructions": "Pay the exact amount and upload a clear transaction proof.",
  "shippingEnabled": true,
  "shippingCharge": 50,
  "freeShippingAbove": 999
}

Discount code document ID is the actual code, e.g. SPARK10:
{
  "active": true,
  "type": "percent",
  "value": 10,
  "minOrder": 0,
  "usageLimit": 100,
  "usedCount": 0,
  "startAt": null,
  "endAt": null
}

IMPORTANT:
- Payment proof is only a submission. The order stays payment_verification_pending until an admin verifies the actual payment.
- Merge the rules into your EXISTING full Firestore/Storage rules. Do not replace unrelated collection rules with these additions.
- Admin.html still needs Store Settings, QR upload, discount-code CRUD, and kit-order verification controls added to its existing admin UI.
- Do not hard-code a personal payment QR in public HTML.
- Confirm the legally applicable GST rate, GSTIN/invoice setup, seller identity and consumer policy with the responsible adult/business/tax professional before selling.


CURRENT CHECKOUT DEFAULTS:
- Delivery is India-only; country is fixed to India and a valid 6-digit PIN is required.
- Default flat shipping charge is ₹80 when storeSettings/main does not override it. Change shippingCharge in storeSettings/main to your actual charge.
- A checkout toast appears immediately when the checkout page opens.
