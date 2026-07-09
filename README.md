# 💧 Water Delivery API

A scalable backend system for managing water delivery operations, built with **FastAPI** and designed for real-world logistics workflows — order management, WhatsApp-based ordering, and location-aware delivery via Google Maps.

This project demonstrates production-style backend development: REST API design, webhook handling, third-party API integration, and clean, migration-backed database architecture.

---

## 🚀 Key Features

**Order Management**
- Full CRUD for water orders (tanker/jug sizing, quantities, pricing)
- Order status tracking: `pending → confirmed → shipped → delivered`

**WhatsApp Business API Integration**
- Receive incoming orders/messages via webhooks
- Send automated replies, order confirmations, and delivery notifications
- Interactive menus for product selection and address input

**Google Maps API Integration**
- Address autocomplete and validation
- Geocoding (address → coordinates)
- Distance/duration calculation for delivery pricing and ETA
- Delivery zone restriction (only serve within defined service areas)

**Developer Experience**
- Auto-generated interactive API docs — Swagger UI (`/docs`) and ReDoc (`/redoc`)
- Modular, clean architecture (models, schemas, CRUD, utilities separated)
- Database migrations via Alembic

---

## 🛠️ System Architecture

| Layer | Technology |
|---|---|
| Framework | FastAPI (Python 3.10+) |
| ORM | SQLAlchemy |
| Database | PostgreSQL |
| Migrations | Alembic |
| Validation | Pydantic |
| Auth | JWT |
| Dev Server | Uvicorn |
| Production Server | Gunicorn |
| Integrations | WhatsApp Business Cloud API, Google Maps Places & Distance Matrix API |

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/SixtusNnanna/water-delivery-api.git
cd water-delivery-api
```

**2. Set up a virtual environment**
```bash
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Configure environment variables**
```bash
cp .env.example .env
```
Then fill in `.env`:
```env
DATABASE_URL=postgresql://user:password@localhost:5432/water_delivery

# JWT
SECRET_KEY=your_very_strong_secret
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440

# WhatsApp Business API
WHATSAPP_TOKEN=your_whatsapp_business_token
WHATSAPP_PHONE_ID=your_phone_number_id
WHATSAPP_WEBHOOK_VERIFY_TOKEN=your_verify_token

# Google Maps API
GOOGLE_MAPS_API_KEY=your_google_maps_key
```

**5. Run database migrations**
```bash
alembic upgrade head
```

**6. Start the server**
```bash
uvicorn app.main:app --reload
```

**7. Expose the webhook locally (development only)**
```bash
ngrok http 8000
```
Use the generated ngrok URL as your WhatsApp webhook callback URL in the Meta Developer dashboard.

---

## 📖 API Documentation

Once running, explore the full interactive API docs:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

---

## 🗺️ Roadmap

- [ ] Paystack payment integration
- [ ] Automated driver assignment logic
- [ ] Admin dashboard for order/driver monitoring

---

## 👤 Author

**Sixtus Omeje**
Backend Developer — Python / FastAPI
[LinkedIn](https://linkedin.com/62s) · [GitHub](https://github.com/SixtusNnanna)
