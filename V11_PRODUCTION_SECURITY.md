# V11 — Production Integration & Security

## Provider integration
- Paystack backend client: initialize + verify.
- VTpass backend client: service categories, service IDs and variation codes.
- Production secrets are environment variables only.
- Sandbox/production is selected by backend configuration.

## Payment safety
1. Create a unique internal funding reference.
2. Initialize Paystack from the backend.
3. Complete checkout in the client.
4. Verify the reference on the backend.
5. Match expected amount/currency/reference.
6. Credit wallet exactly once.
7. Keep an immutable wallet ledger.
8. Process Paystack webhook with signature verification and idempotency.

## VTpass safety
- Never trust a price supplied by the client.
- Resolve current service/variation and server-side price.
- Use Idempotency-Key for every purchase.
- Debit/hold wallet atomically.
- Requery pending transactions.
- Reverse/refund on confirmed failure.

## NIN/BVN
- Use only an authorized verification provider and lawful access.
- Keep provider credentials on backend.
- Restrict endpoint by role.
- Mask sensitive data.
- Record audit events.
- Do not retain more identity information than necessary.

## Release gate
This package is source/configuration work, not a signed production AAB.
Before public launch: configure credentials, deploy HTTPS backend + PostgreSQL, run sandbox tests, security review, Play compliance, and signed AAB build.
