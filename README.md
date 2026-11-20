# 🍕 RVG Gourmet Delivery — Full-Stack Food Ordering & Kitchen Admin System

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x%2F3.x-black?style=for-the-badge&logo=flask&logoColor=white)
![Frontend](https://img.shields.io/badge/Frontend-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-orange?style=for-the-badge)
![Database](https://img.shields.io/badge/Storage-JSON%20Flat--File-green?style=for-the-badge)

**RVG Gourmet Delivery** is a lightweight, mobile-first full-stack food ordering web application and restaurant management suite built with **Python (Flask)**[span_4](start_span)[span_4](end_span)[span_5](start_span)[span_5](end_span). It features a sleek customer storefront with direct **UPI Intent / Dynamic QR payments**, **strict 12-digit UTR anti-fraud validation**, and a real-time **Kitchen Partner Admin Panel**[span_6](start_span)[span_6](end_span)[span_7](start_span)[span_7](end_span)[span_8](start_span)[span_8](end_span).

---

## ✨ Key Features

### 📱 Customer Storefront (`/`)
* **Mobile-First App UI:** Responsive, app-like interface with sticky headers, category pills, and bottom tab navigation[span_9](start_span)[span_9](end_span).
* **Live Search & Filtering:** Instant search across dishes and descriptions alongside category filters (*Pizza, Burger, Drinks*)[span_10](start_span)[span_10](end_span)[span_11](start_span)[span_11](end_span).
* **Interactive Cart & Checkout:** Floating cart summary bar with dynamic quantity steppers (`+` / `-`) and checkout drawer[span_12](start_span)[span_12](end_span).
* **Smart UPI Payment Gateway:** 
  * Generates dynamic `upi://pay` intent links (compatible with PhonePe, GPay, Paytm) and live QR codes[span_13](start_span)[span_13](end_span)[span_14](start_span)[span_14](end_span).
  * Supports custom admin-uploaded QR scanner images[span_15](start_span)[span_15](end_span)[span_16](start_span)[span_16](end_span)[span_17](start_span)[span_17](end_span).
* **Anti-Fraud UTR Verification:** Enforces an exact **12-digit numeric UTR/Ref number** and blocks duplicate UTR submissions across orders[span_18](start_span)[span_18](end_span)[span_19](start_span)[span_19](end_span).
* **User Accounts & Order Tracking:** Session-based login/registration with SHA-256 salted password hashing and live order status tracking[span_20](start_span)[span_20](end_span)[span_21](start_span)[span_21](end_span).

### 🛠️ Kitchen Partner Admin Panel (`/admin`)
* **Protected Admin Gate:** Session-authenticated dark-mode dashboard for restaurant managers[span_22](start_span)[span_22](end_span)[span_23](start_span)[span_23](end_span).
* **Live Order & UTR Verification:** Auto-refreshing order queue highlighting customer UTR numbers so staff can verify payments and approve (`Preparing`) or reject fake UTR orders[span_24](start_span)[span_24](end_span)[span_25](start_span)[span_25](end_span).
* **Order Lifecycle Management:** Track orders from `Payment Pending` $\rightarrow$ `Preparing` $\rightarrow$ `Out for Delivery` $\rightarrow$ `Delivered` / `Cancelled`[span_26](start_span)[span_26](end_span)[span_27](start_span)[span_27](end_span).
* **Full Menu CRUD:** Add, edit, or delete food items with live image previews, categories, and pricing[span_28](start_span)[span_28](end_span)[span_29](start_span)[span_29](end_span).
* **Customer Management:** View registered users, search by phone/name, and block/unblock abusive accounts[span_30](start_span)[span_30](end_span)[span_31](start_span)[span_31](end_span).
* **Dynamic Payment Settings:** Update receiving UPI VPA, payee name, or upload a custom QR scanner image directly from the browser[span_32](start_span)[span_32](end_span)[span_33](start_span)[span_33](end_span).

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
```

---

## 🚀 Getting Started (Local Setup)

### 1. Clone the Repository
```bash
git clone [https://github.com/YOUR_USERNAME/rvg-gourmet-delivery.git](https://github.com/YOUR_USERNAME/rvg-gourmet-delivery.git)
cd rvg-gourmet-delivery
```

### 2. Create a Virtual Environment (Recommended)
```bash
python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Application
```bash
python main.py
```
The server will start on `http://127.0.0.1:5000`[span_34](start_span)[span_34](end_span):
* **Customer Storefront:** `http://127.0.0.1:5000/`[span_35](start_span)[span_35](end_span)
* **Admin Panel:** `http://127.0.0.1:5000/admin`[span_36](start_span)[span_36](end_span)

---

## 🔐 Default Admin Credentials

| Field | Default Value |
| :--- | :--- |
| **Admin URL** | `/admin`[span_37](start_span)[span_37](end_span) |
| **Username** | `admin`[span_38](start_span)[span_38](end_span)[span_39](start_span)[span_39](end_span) |
| **Password** | `rvg@123`[span_40](start_span)[span_40](end_span)[span_41](start_span)[span_41](end_span) |

> ⚠️ **Security Note:** Before deploying to production, update `ADMIN_USER`, `ADMIN_PASS`, and `app.secret_key` inside `main.py`[span_42](start_span)[span_42](end_span) (or load them via environment variables).

---

## 🔌 Core API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/menu` | Fetch all available menu items[span_43](start_span)[span_43](end_span) |
| `POST` | `/api/auth/register` | Register a new customer account[span_44](start_span)[span_44](end_span) |
| `POST` | `/api/auth/login` | Authenticate customer session[span_45](start_span)[span_45](end_span) |
| `POST` | `/api/payment/generate-upi` | Calculate cart total & generate UPI payment payload[span_46](start_span)[span_46](end_span) |
| `POST` | `/api/place-order` | Validate 12-digit unique UTR & create order[span_47](start_span)[span_47](end_span) |
| `GET` | `/api/user/orders` | Retrieve logged-in customer's order history[span_48](start_span)[span_48](end_span) |
| `POST` | `/api/admin/login` | Authenticate admin session[span_49](start_span)[span_49](end_span) |
| `GET` | `/api/admin/orders` | Fetch all live and historical orders *(Admin)*[span_50](start_span)[span_50](end_span) |
| `POST` | `/api/admin/update-status` | Update order & payment verification status *(Admin)*[span_51](start_span)[span_51](end_span) |
| `POST` | `/api/admin/settings/update` | Update UPI VPA, Payee Name, or Custom QR *(Admin)*[span_52](start_span)[span_52](end_span) |

---

## 🌐 Deployment

This project includes a `Procfile` (`web: gunicorn main:app`)[span_53](start_span)[span_53](end_span) and is ready for one-click deployment on platforms like **Render**, **Railway**, **PythonAnywhere**, or **Heroku**.

---

## 📄 License

This project is licensed under the **MIT License** — feel free to use, modify, and distribute it.
