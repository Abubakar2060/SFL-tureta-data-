# SFL TURETA DATA Backend V1 API

Base path: `/api/v1`

## Auth
- POST `/auth/register`
- POST `/auth/login`
- GET `/auth/me`

## Wallet
- GET `/wallet`
- POST `/wallet/fund` — reserved for Paystack integration

## Data
- GET `/data/networks`
- GET `/data/plans?network=mtn`
- POST `/data/purchase`

## Transactions
- GET `/transactions`

## Admin
- GET `/admin/dashboard`

## Security
- Send `Authorization: Bearer <access_token>`.
- Data purchases require `Idempotency-Key`.
- Never put Paystack/provider secret keys in the Android APK.
- Prices and roles must be controlled by the backend.
- Production wallet changes must use DB transactions/row locking.
