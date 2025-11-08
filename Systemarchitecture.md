The Technical Blueprint of My Approach for Releaf
Goal: Support ordering, loan request, offline-capable flow, and USSD for feature-phone user

Components include;
1. Frontend (Web and Mobile)
- Web: React (Vercel deploy)
- Mobile: React Native/ Expo (Android-first)
Resposibilities are; signup, order UI, reviewa, offline catching
2. Backend API
- Node.js + Express
- Endpoint: /auth, /user, /order, /products, /loans, /reviews
3. Database
- Mongodp for users,products, order, loans, review
4. Object Storage
- AWS S3 bucket for images, invoices, KYC docs
5. Cache / Queue
- Redis for sessions and queues; worker (Celery) for background tasks
6. USSD Gateway
- Integrate Africa's Talking or local provider; USSD - webhook - backend
7. Payments
- Paystack with webhook to confirm payment.

Example Order Flow
Step 1. User places order - POST/order
Step 2. Backend validates, creates order in DB
step 3. If payment required, then create payment session and user pays
step 4. On webhook success - mark order paid and enqueue delivery job

Offline and USSD
a) Frontend caches product catalog for offline browsing.
b) USSD maps ti same order endpoints; reconciliation worker syncs USSD order with DB

Security and Privacy
- TLS everywhere, Session Cookies, PII encrypted at rest
- Allow users to hide their phone number/ email in settings i.e toggle button is created for easy access

Why this is feasible
- It uses proves tech (React, Node, Mongodp). USSD and offline patterns are common in Afrcian markets and supported by Redis-backed session handling and background reconciliataion. 


