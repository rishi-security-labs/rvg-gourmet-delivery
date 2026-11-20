# 🍕 RVG Gourmet Delivery — Full-Stack Food Ordering & Kitchen Admin System

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x%2F3.x-black?style=for-the-badge&logo=flask&logoColor=white)
![Frontend](https://img.shields.io/badge/Frontend-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-orange?style=for-the-badge)
![Database](https://img.shields.io/badge/Storage-JSON%20Flat--File-green?style=for-the-badge)

**RVG Gourmet Delivery** is a lightweight, mobile-first full-stack food ordering web application and restaurant management suite built with **Python (Flask)**[span_0](start_span)[span_0](end_span)[span_1](start_span)[span_1](end_span). It features a sleek customer storefront with direct **UPI Intent / Dynamic QR payments**, **strict 12-digit UTR anti-fraud validation**, and a real-time **Kitchen Partner Admin Panel**[span_2](start_span)[span_2](end_span)[span_3](start_span)[span_3](end_span)[span_4](start_span)[span_4](end_span).

---

## ✨ Key Features

### 📱 Customer Storefront (`/`)
* **Mobile-First App UI:** Responsive, app-like interface with sticky headers, category pills, and bottom tab navigation[span_5](start_span)[span_5](end_span).
* **Live Search & Filtering:** Instant search across dishes and descriptions alongside category filters (*Pizza, Burger, Drinks*)[span_6](start_span)[span_6](end_span)[span_7](start_span)[span_7](end_span).
* **Interactive Cart & Checkout:** Floating cart summary bar with dynamic quantity steppers (`+` / `-`) and checkout drawer[span_8](start_span)[span_8](end_span).
* **Smart UPI Payment Gateway:** 
  * Generates dynamic `upi://pay` intent links (compatible with PhonePe, GPay, Paytm) and live QR codes[span_9](start_span)[span_9](end_span)[span_10](start_span)[span_10](end_span).
  * Supports custom admin-uploaded QR scanner images[span_11](start_span)[span_11](end_span)[span_12](start_span)[span_12](end_span)[span_13](start_span)[span_13](end_span).
* **Anti-Fraud UTR Verification:** Enforces an exact **12-digit numeric UTR/Ref number** and blocks duplicate UTR submissions across orders[span_14](start_span)[span_14](end_span)[span_15](start_span)[span_15](end_span).
* **User Accounts & Order Tracking:** Session-based login/registration with SHA-256 salted password hashing and live order status tracking[span_16](start_span)[span_16](end_span)[span_17](start_span)[span_17](end_span).

### 🛠️ Kitchen Partner Admin Panel (`/admin`)
* **Protected Admin Gate:** Session-authenticated dark-mode dashboard for restaurant managers[span_18](start_span)[span_18](end_span)[span_19](start_span)[span_19](end_span).
* **Live Order & UTR Verification:** Auto-refreshing order queue highlighting customer UTR numbers so staff can verify payments and approve (`Preparing`) or reject fake UTR orders[span_20](start_span)[span_20](end_span)[span_21](start_span)[span_21](end_span).
* **Order Lifecycle Management:** Track orders from `Payment Pending` $\rightarrow$ `Preparing` $\rightarrow$ `Out for Delivery` $\rightarrow$ `Delivered` / `Cancelled`[span_22](start_span)[span_22](end_span)[span_23](start_span)[span_23](end_span).
* **Full Menu CRUD:** Add, edit, or delete food items with live image previews, categories, and pricing[span_24](start_span)[span_24](end_span)[span_25](start_span)[span_25](end_span).
* **Customer Management:** View registered users, search by phone/name, and block/unblock abusive accounts[span_26](start_span)[span_26](end_span)[span_27](start_span)[span_27](end_span).
* **Dynamic Payment Settings:** Update receiving UPI VPA, payee name, or upload a custom QR scanner image directly from the browser[span_28](start_span)[span_28](end_span)[span_29](start_span)[span_29](end_span).

---

## 📂 Project Structure

```text
rvg-gourmet-delivery/
├── main.py              # Flask backend, REST APIs, auth, & UTR validation logic
├── index.html           # Customer mobile storefront UI & client logic
├── admin.html           # Kitchen partner admin dashboard UI
├── requirements.txt     # Python dependencies (Flask, gunicorn)
├── Procfile             # Deployment configuration for Render / Heroku / Railway
├── README.md            # Project documentation
├── .gitignore           # Ignored files and runtime database folder
└── database/            # Auto-generated JSON storage (users, menu, orders, settings)
