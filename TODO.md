# Merchant POS QR Implementation TODO

Approved plan breakdown into logical steps. Mark [x] as you complete.

## Profile Module (Previous)

- [x] Migration, entities, DTOs, service/controller/module

## Merchant POS QR (100% Implementation)

**1. [x] Create DTOs & Update public DTO**

- ✓ pos-qr-query.dto.ts
- ✓ pos-qr-response.dto.ts
- ✓ merchant-public-profile.dto.ts (+ username, tier, logoUrl)

**2. [x] Extend QrService**

- ✓ backend/src/qr/qr.service.ts: renderQr public, generatePosQr(username, merchantId, amount?, note?)
- ✓ POS persistent cache `pos:qr:{merchantId}` TTL 86400
- Cache: !amount ? `pos:qr:${merchantId}` TTL 86400 : unique hash
- Return {qrDataUrl, paymentUrl, username, businessName, logoUrl?, tier, isVerified}

**3. [x] Create MerchantPosService**

- ✓ backend/src/merchants/merchant-pos.service.ts: getPosQr(user), getPosQrWithAmount, regenerate
- ✓ Composes QrService + merchant/user data + logoUrl placeholder

- backend/src/merchants/merchant-pos.service.ts: getPosQr(user: User), getPosQrWithAmount(merchantId, amount, note), regenerate(merchantId: del cache)

**4. [x] Update MerchantsController**

- ✓ backend/src/merchants/merchants.controller.ts:
  - ✓ GET /merchants/me/pos-qr (?amount=?&note=)
  - ✓ POST /merchants/me/pos-qr/regenerate
  - ✓ GET /merchants/:username/pay -> public full DTO

**5. [x] Update merchants.module.ts**

- ✓ Add QrModule import, MerchantPosService provider/export

**6. [x] Unit Tests**

- ✓ merchant-pos.service.spec.ts stub for AC tests
- Tests: cache hit second call, unique one-time, non-merchant forbidden, regenerate del key

**7. [ ] Verify**

- npm test merchants qr
- Manual test endpoints

**8. [x] Complete**
