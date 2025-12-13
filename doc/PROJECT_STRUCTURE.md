# BestBuddies Pet Grooming - Project Structure

## Overview

This document explains the project structure to help new team members understand the codebase organization.

```
test-main/
├── public/                          # Public-facing pages (customer entry points)
│   ├── index.html                   # Home page
│   ├── login.html                   # Login page
│   ├── signup.html                  # Registration page
│   ├── services.html                # Services listing
│   ├── reviews.html                 # Customer reviews
│   └── policy.html                  # Privacy/Terms policy
│
├── firebase/                        # Firebase configuration and database
│   ├── firebase-config.js           # Firebase initialization
│   ├── firebase-db.js               # Database operations
│   ├── bestbuddiespetshop-default-rtdb-.json  # Firebase backup
│   └── FIREBASE_SETUP_INSTRUCTIONS.md
│
├── js/                              # JavaScript modules
│   ├── Core Modules (Refactored)
│   │   ├── booking-state.js         # State management
│   │   ├── booking-logic.js         # Business logic
│   │   ├── booking-ui.js            # UI rendering
│   │   ├── booking-events.js        # Event handling
│   │   ├── modal-system.js          # Modal component
│   │   └── booking-integration.js   # Integration layer
│   │
│   ├── Page Logic
│   │   ├── booking.js               # Booking page logic
│   │   ├── admin.js                 # Admin dashboard logic
│   │   ├── customer.js              # Customer dashboard logic
│   │   ├── groomer.js               # Groomer dashboard logic
│   │   └── staff.js                 # Staff dashboard logic
│   │
│   ├── Utilities
│   │   ├── auth.js                  # Authentication
│   │   ├── main.js                  # Global utilities
│   │   └── custom-alert.js          # Alert component
│   │
│   ├── Tests
│   │   ├── Unit Tests
│   │   │   ├── booking-state.test.js
│   │   │   ├── booking-logic.test.js
│   │   │   ├── booking-ui.test.js
│   │   │   ├── booking-events.test.js
│   │   │   ├── modal-system.test.js
│   │   │   ├── booking-form-input.test.js
│   │   │   └── booking-form-input-integration.test.js
│   │   │
│   │   └── Property-Based Tests
│   │       ├── booking-state.pbt.js
│   │       ├── booking-logic.pbt.js
│   │       └── booking-events.pbt.js
│   │
│   └── Integration
│       ├── booking-integration-example.js
│       └── booking-consolidation.test.js
│
├── css/                             # Stylesheets
│   ├── styles.css                   # Global styles
│   ├── components.css               # Component styles
│   ├── booking.css                  # Booking page styles
│   ├── admin-dashboard.css          # Admin dashboard styles
│   ├── customer-dashboard.css       # Customer dashboard styles
│   ├── groomer-dashboard.css        # Groomer dashboard styles
│   ├── staff-dashboard.css          # Staff dashboard styles
│   ├── login.css                    # Login page styles
│   ├── signup.css                   # Signup page styles
│   ├── policy.css                   # Policy page styles
│   ├── index.css                    # Home page styles
│   └── custom-alert.css             # Alert component styles
│
├── assets/                          # Images and media
│   ├── logo.png                     # Logo
│   ├── 1.jpg - 8.jpg                # Gallery images
│   └── pics.jpg                     # Additional images
│
├── doc/                             # Documentation
│   └── CONSOLIDATION_TEST_GUIDE.md
│
├── scripts/                         # Utility scripts
│   └── dedupe-booking.js            # Data deduplication
│
├── HTML Pages (Dashboard/Special Pages)
│   ├── booking.html                 # Booking flow page
│   ├── booking-success.html         # Booking confirmation
│   ├── admin-dashboard.html         # Admin interface
│   ├── customer-dashboard.html      # Customer interface
│   ├── groomer-dashboard.html       # Groomer interface
│   ├── groomer-setup-tool.html      # Groomer setup
│   ├── fix-groomer-roles.html       # Admin tool
│   ├── pbt-runner.html              # Test runner
│   ├── test-runner.html             # Test runner
│   └── README.md                    # Project README
│
└── Configuration
    └── _config.yml                  # Jekyll configuration
```

## Key Folders Explained

### `/public` - Public Pages
These are the customer-facing entry points. They should be accessible without authentication.

**Files:**
- `index.html` - Home page with service overview
- `login.html` - User login
- `signup.html` - User registration
- `services.html` - Service catalog
- `reviews.html` - Customer testimonials
- `policy.html` - Privacy and terms

**Access:** Direct URL or from navigation menu

### `/firebase` - Firebase Configuration
Contains all Firebase-related configuration and database operations.

**Files:**
- `firebase-config.js` - Firebase project configuration (API keys, project ID)
- `firebase-db.js` - Database operations (CRUD, queries)
- `FIREBASE_SETUP_INSTRUCTIONS.md` - Setup guide

**Usage:** Imported by all pages that need database access

### `/js` - JavaScript Modules

#### Core Refactored Modules
These implement the new modular architecture:
- `booking-state.js` - Centralized state management
- `booking-logic.js` - Pure business logic
- `booking-ui.js` - Pure rendering functions
- `booking-events.js` - Event system
- `modal-system.js` - Reusable modal component
- `booking-integration.js` - Orchestration

#### Page Logic
Each dashboard/page has its own logic file:
- `booking.js` - Booking flow orchestration
- `admin.js` - Admin dashboard features
- `customer.js` - Customer dashboard features
- `groomer.js` - Groomer dashboard features
- `staff.js` - Staff dashboard features

#### Tests
Comprehensive test suite:
- Unit tests for each module
- Property-based tests for universal properties
- Integration tests for complete flows

### `/css` - Stylesheets
Organized by page/component:
- Global styles in `styles.css`
- Component styles in `components.css`
- Page-specific styles in separate files

### `/assets` - Media Files
Images and other media used throughout the site.

## Import Paths

### From HTML Files
```html
<!-- Public pages (in /public) -->
<script src="../js/main.js"></script>
<script src="../firebase/firebase-config.js"></script>
<script src="../firebase/firebase-db.js"></script>

<!-- Dashboard pages (in root) -->
<script src="js/main.js"></script>
<script src="firebase/firebase-config.js"></script>
<script src="firebase/firebase-db.js"></script>
```

### From JavaScript Files
```javascript
// In /js files
import { getBookings } from '../firebase/firebase-db.js';

// In /firebase files
// No imports needed (standalone)
```

## Data Flow

```
User Browser
    ↓
Public Pages (/public)
    ↓
Authentication (auth.js)
    ↓
Dashboard Pages (root)
    ↓
Page Logic (js/admin.js, js/booking.js, etc.)
    ↓
Core Modules (booking-state.js, booking-logic.js, etc.)
    ↓
Firebase (firebase/firebase-db.js)
    ↓
Firebase Database
```

## Adding New Features

### 1. New Public Page
- Create in `/public/new-page.html`
- Link from `/public/index.html`
- Import styles from `../css/`
- Import scripts from `../js/`

### 2. New Dashboard Feature
- Create page in root: `new-dashboard.html`
- Create logic in `/js/new-dashboard.js`
- Import from `js/` and `firebase/`
- Add to navigation in relevant dashboard

### 3. New Module
- Create in `/js/new-module.js`
- Export functions/classes
- Import in pages that need it
- Create tests in `/js/new-module.test.js`

### 4. New Utility
- Create in `/js/utils/` (if multiple utilities)
- Export functions
- Import where needed

## Testing

### Unit Tests
Run individual test files:
```bash
npm test -- js/booking-state.test.js
```

### Property-Based Tests
Run in browser:
```
Open pbt-runner.html
```

### Integration Tests
Test complete flows manually or with integration test files.

## Deployment

### Development
```bash
npm run dev
# Serves from test-main/
```

### Production
```bash
npm run build
# Builds from test-main/
# Deploys public/ as root
```

## Quick Reference

| Need | Location |
|------|----------|
| Add public page | `/public/` |
| Add Firebase function | `/firebase/firebase-db.js` |
| Add page logic | `/js/page-name.js` |
| Add utility | `/js/utils/` or `/js/` |
| Add styles | `/css/` |
| Add images | `/assets/` |
| Add tests | `/js/` with `.test.js` suffix |
| Add PBT tests | `/js/` with `.pbt.js` suffix |

## Notes for New Team Members

1. **Always use relative paths** - Makes code portable
2. **Keep modules small** - Each file should have one responsibility
3. **Write tests** - Every new function should have tests
4. **Use the state manager** - Don't mutate global state
5. **Escape user input** - Prevent XSS attacks
6. **Document your code** - Add JSDoc comments
7. **Follow the patterns** - Look at existing code for examples

