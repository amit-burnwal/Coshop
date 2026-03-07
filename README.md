# CoShop — Marketplace Platform

CoShop is a marketplace platform that empowers Small and Medium-sized Enterprises (SMEs) by providing an integrated online presence to connect SMEs with consumers.

---

## Project structure
```
coshop-marketplace/
├── backend/              # Node.js + Express backend API
│   ├── src/
│   │   ├── config/      # Database and Redis configuration
│   │   ├── services/    # Business logic services
│   │   ├── models/      # Data models
│   │   ├── middleware/  # Authentication and validation
│   │   ├── routes/      # API route handlers
│   │   └── utils/       # Utility functions
│   ├── tests/           # Unit and integration tests
│   └── package.json
├── frontend/            # React frontend application
│   ├── src/
│   │   ├── components/  # Reusable React components
│   │   ├── pages/       # Page components
│   │   ├── services/    # API client services
│   │   ├── store/       # State management
│   │   └── utils/       # Utility functions
│   └── package.json
├── database/            # Database initialization scripts
│   ├── init.sql         # PostgreSQL + PostGIS schema
│   └── README.md
└── .kiro/specs/         # Project specifications
    └── coshop-marketplace/
        ├── requirements.md
        ├── design.md
        └── tasks.md
```

---

## Technology stack

### Backend
- Node.js + Express
- PostgreSQL with PostGIS
- Redis
- JWT authentication
- WebSocket (planned/real-time features)

### Frontend
- React.js
- Tailwind CSS
- React Router
- Leaflet (maps)
- Zustand (state management)

### External integrations (planned/partial)
- Stripe / PayPal / M-Pesa (payments)
- Uber API, Pick Up Mtaani (delivery)
- Google Maps API (geolocation)

---

## Getting started

### Prerequisites
- Node.js 18+ and npm
- PostgreSQL 14+ with PostGIS
- Redis 6+

### Backend setup
1. cd backend
2. npm install
3. copy .env.example .env
4. Update .env
5. npm run dev
- Backend runs at: http://localhost:5000

### Frontend setup
1. cd frontend
2. npm install
3. copy .env.example .env
4. Update .env
5. npm run dev
- Frontend runs at: http://localhost:3000

### Database setup
1. createdb coshop_db
2. psql -d coshop_db -f database/init.sql
- See database/README.md for details

---

## Development

### Running tests
- Backend: cd backend && npm test
- Frontend: cd frontend && npm test

### Code quality
- Minimum 80% coverage for business logic
- ESLint + Prettier

---

## Implementation status

### ✅ Completed (Backend core)
Highlights:
- Authentication & Authorization (register, login, JWT, refresh, RBAC)
- Business management (CRUD, automatic geocoding, PostGIS POINT storage)
- Product management (CRUD, inventory, categories, advanced search, geolocation filters)
- Geolocation services (nearby search, distance calc, forward/reverse geocoding)
- Caching with Redis (search/geocode/geolocation caches + TTLs)
- Validation & error handling (Joi, standardized responses)
- 20 implemented API endpoints across auth, business, product, geolocation

### ⏳ Not implemented / Planned
- Order management & workflow
- Payment gateways
- Delivery integrations
- Bidirectional ratings
- Real-time messaging
- Multi-channel notifications
- Analytics & reporting
- File uploads (images)
- Frontend (only skeleton)
- Business verification, staff management, promotions, wishlist

---

## Key features

Implemented
- Business registration + automatic geocoding
- Product catalog + inventory tracking
- Geolocation-based discovery and searches
- Advanced product search with filters, sorting, pagination
- JWT auth with refresh tokens
- Role-based access control
- Redis caching

Planned
- Order processing & delivery
- Multiple payment processors
- Ratings, messaging, analytics, notifications

---

## API documentation
- Base URL: http://localhost:5000/api/v1
- Implemented endpoints:
  - Authentication (register, login, refresh) — 3 endpoints
  - Business (CRUD, list by owner, list products) — 6 endpoints
  - Product (CRUD, search, inventory update) — 6 endpoints
  - Geolocation (nearby, distance, bounds, geocode, reverse-geocode) — 5 endpoints

See docs/05-api-endpoints.md for full reference and examples.

---

## Documentation
- Quick Start: docs/00-quick-start.md
- Requirements: .kiro/specs/coshop-marketplace/requirements.md
- Design: .kiro/specs/coshop-marketplace/design.md
- Tasks / Roadmap: .kiro/specs/coshop-marketplace/tasks.md
- Architecture: docs/01-architecture-overview.md
- Service Structure: docs/02-service-structure.md
- Database Schema: docs/03-database-schema.md
- Authentication: docs/06-authentication-authorization.md
- Error Handling: docs/07-error-handling.md
- Caching Strategy: docs/08-caching-strategy.md
- Geolocation: docs/06-geolocation-implementation.md
- Documentation index: docs/README.md

---

## License
MIT

Summary (concise)
- Purpose: CoShop is a marketplace platform targeting SMEs to list businesses and products with geolocation-aware search and rich backend features.
- Tech: Node.js/Express backend, PostgreSQL+PostGIS, Redis; React/Tailwind frontend.
- Status: Backend core mostly implemented (auth, business/product CRUD, geolocation, caching, validation). Frontend is a skeleton and many user-facing features (orders, payments, delivery, messaging, uploads, analytics) are not yet implemented.
- Run locally: Start backend on :5000 and frontend on :3000 after installing deps and configuring .env; initialize DB with database/init.sql.
- API: ~20 endpoints implemented across auth, business, product, geolocation. Docs available under docs/.
- Next major work: Order/payment flow, delivery integrations, file uploads, real-time features, complete frontend.

