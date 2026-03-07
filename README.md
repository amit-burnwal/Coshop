# CoShop Marketplace Platform

---------
CoShop is a marketplace platform designed to empower Small and Medium-sized Enterprises (SMEs) by providing them with an integrated online presence. The platform connects SMEs with consumers through business registration, inventory management, and geolocation-based discovery.
---------
## Project Structure

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
│   ├── init.sql        # PostgreSQL + PostGIS schema
│   └── README.md
└── .kiro/specs/        # Project specifications
    └── coshop-marketplace/
        ├── requirements.md
        ├── design.md
        └── tasks.md
```

## Technology Stack

### Backend
- Node.js with Express.js
- PostgreSQL with PostGIS extension
- Redis for caching
- JWT authentication
- WebSocket for real-time features

### Frontend
- React.js
- Tailwind CSS
- React Router
- Leaflet for mapping
- Zustand for state management

### External Integrations
- Stripe/PayPal/M-Pesa for payments
- Uber API, Pick Up Mtaani for delivery
- Google Maps API for geolocation

## Getting Started

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL 14+ with PostGIS
- Redis 6+

### Backend Setup

1. Navigate to backend directory:
```bash
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Copy environment variables:
```bash
copy .env.example .env
```

4. Update `.env` with your configuration

5. Start development server:
```bash
npm run dev
```

The backend API will run on http://localhost:5000

### Frontend Setup

1. Navigate to frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Copy environment variables:
```bash
copy .env.example .env
```

4. Update `.env` with your configuration

5. Start development server:
```bash
npm run dev
```

The frontend will run on http://localhost:3000

### Database Setup

1. Create PostgreSQL database:
```bash
createdb coshop_db
```

2. Run initialization script:
```bash
psql -d coshop_db -f database/init.sql
```

See `database/README.md` for more details.

## Development

### Running Tests

Backend tests:
```bash
cd backend
npm test
```

Frontend tests:
```bash
cd frontend
npm test
```

### Code Quality

- Minimum 80% code coverage for business logic
- ESLint for code linting
- Prettier for code formatting

## Implementation Status

### ✅ Completed (Backend Core)

**Authentication & Authorization:**
- User registration (SME/consumer) with automatic business profile creation for SMEs
- Login with JWT tokens (15min access, 7d refresh)
- Token refresh mechanism
- Role-based access control (SME vs consumer)
- Ownership validation for resource modifications

**Business Management:**
- Full CRUD operations for business profiles
- Automatic geocoding (address → coordinates) via OpenStreetMap/Google Maps
- PostGIS GEOGRAPHY(POINT) storage for efficient spatial queries
- Business location updates with re-geocoding
- List businesses by owner

**Product Management:**
- Full CRUD operations for products
- Inventory tracking with auto-calculated in_stock status
- 15 predefined product categories
- Advanced search with keyword, category, price filters
- Geolocation-based search with distance calculation
- Sorting by price, date, rating, distance
- Pagination support

**Geolocation Services:**
- Nearby business search (radius-based, 0.1-100km)
- Distance calculation between any two points
- Map bounds queries for pan/zoom interactions
- Forward geocoding (address → coordinates)
- Reverse geocoding (coordinates → address)
- PostGIS spatial queries with GIST indexes

**Caching & Performance:**
- Redis integration for frequently accessed data
- Product search results cached (5min TTL)
- Geocoding results cached (24hr TTL)
- Geolocation queries cached (1hr TTL)
- Automatic cache invalidation on data changes

**Data Validation & Error Handling:**
- Joi schemas for all inputs
- Standardized error response format
- Proper HTTP status codes
- Typed exceptions with error codes
- Database transactions for atomic operations

**API Endpoints:** 20 implemented endpoints across authentication, business, product, and geolocation domains

### ⏳ Not Implemented

- Order management and workflow
- Payment processing (Stripe, M-Pesa, PayPal)
- Delivery service integration (Uber, Pick Up Mtaani)
- Bidirectional rating system (consumer↔SME)
- Real-time messaging (WebSocket)
- Multi-channel notifications (email, SMS, push)
- Business analytics and reporting
- File upload for images
- Frontend web application (only skeleton exists)
- Business verification workflow
- Staff account management
- Promotions and discounts
- Favorites/wishlist

## Key Features

### Implemented
- ✅ Business registration with automatic geocoding
- ✅ Product catalog management with inventory tracking
- ✅ Geolocation-based business discovery
- ✅ Advanced product search with filters
- ✅ JWT authentication with refresh tokens
- ✅ Role-based access control
- ✅ Redis caching for performance

### Planned
- ⏳ Order processing with delivery integration
- ⏳ Payment processing (multiple gateways)
- ⏳ Bidirectional rating system
- ⏳ Real-time messaging
- ⏳ Business analytics dashboard
- ⏳ Multi-channel notifications
- ⏳ Business verification workflow

## API Documentation

**Base URL:** `http://localhost:5000/api/v1`

**Implemented Endpoints:**
- Authentication: 3 endpoints (register, login, refresh)
- Business: 6 endpoints (CRUD, list by owner, list products)
- Product: 6 endpoints (CRUD, search, inventory update)
- Geolocation: 5 endpoints (nearby, distance, bounds, geocode, reverse-geocode)

See [docs/05-api-endpoints.md](docs/05-api-endpoints.md) for complete API reference with examples.

## Documentation

### Quick Start
- [Quick Start Guide](docs/00-quick-start.md) - Rapid overview with examples

### Specifications
- [Requirements](.kiro/specs/coshop-marketplace/requirements.md) - Detailed requirements (20 user stories)
- [Design Document](.kiro/specs/coshop-marketplace/design.md) - System design and architecture
- [Implementation Tasks](.kiro/specs/coshop-marketplace/tasks.md) - Development roadmap

### Technical Documentation
- [Architecture Overview](docs/01-architecture-overview.md) - System architecture and design principles
- [Service Structure](docs/02-service-structure.md) - Business logic and service patterns
- [Database Schema](docs/03-database-schema.md) - Complete schema with PostGIS
- [API Endpoints](docs/05-api-endpoints.md) - Complete API reference (20 endpoints)
- [Authentication](docs/06-authentication-authorization.md) - JWT and RBAC implementation
- [Error Handling](docs/07-error-handling.md) - Error patterns and status codes
- [Caching Strategy](docs/08-caching-strategy.md) - Redis caching and performance
- [Geolocation](docs/06-geolocation-implementation.md) - PostGIS spatial queries

See [docs/README.md](docs/README.md) for complete documentation index.

## License

MIT
#   C o s h o p 
 

 
