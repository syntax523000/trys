# BestBuddies Pet Grooming - File Organization Guide

## ✅ Current Organization Status

Your project is now organized with the following structure:

```
test-main/
├── public/                    ✅ Public-facing pages
│   ├── index.html            (Home page)
│   ├── login.html            (Login)
│   ├── signup.html           (Registration)
│   ├── services.html         (Services)
│   ├── reviews.html          (Reviews)
│   └── policy.html           (Privacy/Terms)
│
├── firebase/                 ✅ Firebase configuration
│   ├── firebase-config.js    (Firebase init)
│   ├── firebase-db.js        (Database ops)
│   └── FIREBASE_SETUP_INSTRUCTIONS.md
│
├── js/                       ✅ JavaScript modules
│   ├── Core Modules
│   │   ├── booking-state.js
│   │   ├── booking-logic.js
│   │   ├── booking-ui.js
│   │   ├── booking-events.js
│   │   ├── modal-system.js
│   │   └── booking-integration.js
│   │
│   ├── Page Logic
│   │   ├── booking.js
│   │   ├── admin.js
│   │   ├── customer.js
│   │   ├── groomer.js
│   │   └── staff.js
│   │
│   ├── Utilities
│   │   ├── auth.js
│   │   ├── main.js
│   │   └── custom-alert.js
│   │
│   └── Tests
│       ├── booking-state.test.js
│       ├── booking-logic.test.js
│       ├── booking-ui.test.js
│       ├── booking-events.test.js
│       ├── modal-system.test.js
│       ├── booking-form-input.test.js
│       ├── booking-form-input-integration.test.js
│       ├── booking-state.pbt.js
│       ├── booking-logic.pbt.js
│       ├── booking-events.pbt.js
│       ├── booking-consolidation.test.js
│       └── booking-integration-example.js
│
├── css/                      ✅ Stylesheets
│   ├── styles.css
│   ├── components.css
│   ├── booking.css
│   ├── admin-dashboard.css
│   ├── customer-dashboard.css
│   ├── groomer-dashboard.css
│   ├── staff-dashboard.css
│   ├── login.css
│   ├── signup.css
│   ├── policy.css
│   ├── index.css
│   └── custom-alert.css
│
├── assets/                   ✅ Images and media
│   ├── logo.png
│   ├── 1.jpg - 8.jpg
│   └── pics.jpg
│
├── doc/                      ✅ Documentation
│   └── CONSOLIDATION_TEST_GUIDE.md
│
├── scripts/                  ✅ Utility scripts
│   └── dedupe-booking.js
│
├── Dashboard/Special Pages   ✅ Root level
│   ├── booking.html
│   ├── booking-success.html
│   ├── admin-dashboard.html
│   ├── customer-dashboard.html
│   ├── groomer-dashboard.html
│   ├── groomer-setup-tool.html
│   ├── fix-groomer-roles.html
│   ├── pbt-runner.html
│   └── test-runner.html
│
└── Configuration
    ├── _config.yml
    ├── PROJECT_STRUCTURE.md      ✅ NEW
    └── ORGANIZATION_GUIDE.md     ✅ NEW
```

## 📋 Path Reference for Developers

### Public Pages (in `/public/`)
When linking to resources from public pages, use `../` to go up one level:

```html
<!-- CSS -->
<link rel="stylesheet" href="../css/styles.css">

<!-- JavaScript -->
<script src="../js/main.js"></script>
<script src="../firebase/firebase-config.js"></script>

<!-- Images -->
<img src="../assets/logo.png" alt="Logo">
```

### Dashboard Pages (in root `/`)
When linking to resources from dashboard pages, use direct paths:

```html
<!-- CSS -->
<link rel="stylesheet" href="css/styles.css">

<!-- JavaScript -->
<script src="js/main.js"></script>
<script src="firebase/firebase-config.js"></script>

<!-- Images -->
<img src="assets/logo.png" alt="Logo">
```

### JavaScript Files (in `/js/`)
When importing from JavaScript files:

```javascript
// From /js files to /firebase
import { getBookings } from '../firebase/firebase-db.js';

// From /js files to other /js files
import { BookingStateManager } from './booking-state.js';
```

## 🔄 Data Flow Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    User Browser                              │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              Public Pages (/public)                          │
│  index.html → login.html → signup.html → services.html      │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│           Authentication Layer (auth.js)                     │
│  Validates user credentials and manages sessions            │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│         Dashboard Pages (root directory)                     │
│  booking.html → admin-dashboard.html → customer-dashboard   │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│          Page Logic (/js/page-name.js)                       │
│  booking.js → admin.js → customer.js → groomer.js           │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│      Core Modules (/js/booking-*.js)                         │
│  State → Logic → UI → Events → Modal System                 │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│        Firebase Layer (/firebase/firebase-db.js)             │
│  Database operations (CRUD, queries, transactions)          │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│              Firebase Database (Cloud)                       │
│  Realtime Database with authentication and rules            │
└─────────────────────────────────────────────────────────────┘
```

## 📁 Folder Responsibilities

### `/public` - Customer Entry Points
**Purpose:** Public-facing pages accessible without authentication
**Responsibility:** 
- Display service information
- Handle user registration and login
- Provide navigation to booking system

**Files:**
- `index.html` - Home page with hero section and service overview
- `login.html` - User login form
- `signup.html` - User registration form
- `services.html` - Detailed service catalog
- `reviews.html` - Customer testimonials and reviews
- `policy.html` - Privacy policy and terms of service

**Import Pattern:** Use `../` to reference parent directory resources

---

### `/firebase` - Backend Configuration
**Purpose:** Centralized Firebase configuration and database operations
**Responsibility:**
- Initialize Firebase project
- Manage database connections
- Provide CRUD operations
- Handle authentication tokens

**Files:**
- `firebase-config.js` - Firebase project configuration (API keys, project ID, auth domain)
- `firebase-db.js` - All database operations (getBookings, saveBooking, updateBooking, etc.)
- `FIREBASE_SETUP_INSTRUCTIONS.md` - Setup guide for new developers

**Import Pattern:** 
```javascript
import { getBookings, saveBooking } from '../firebase/firebase-db.js';
```

---

### `/js` - Application Logic

#### Core Modules (Refactored Architecture)
**Purpose:** Implement the new modular booking system

- **booking-state.js** - Centralized immutable state management
  - Manages all booking data
  - Provides state change notifications
  - Maintains state history for debugging

- **booking-logic.js** - Pure business logic (no DOM dependencies)
  - Validation functions (phone, age, step requirements)
  - Calculation functions (pricing, filtering)
  - State transition logic

- **booking-ui.js** - Pure rendering functions
  - Generates HTML strings from state
  - Handles XSS prevention (HTML escaping)
  - Deterministic rendering (same input = same output)

- **booking-events.js** - Event system
  - Connects DOM events to state updates
  - Validates input before state changes
  - Triggers side effects (load packages, render UI)

- **modal-system.js** - Reusable modal component
  - Configuration-driven modal creation
  - Event listener cleanup
  - Focus management
  - Promise-based API

- **booking-integration.js** - Orchestration layer
  - Initializes all modules
  - Connects state manager to event system
  - Manages UI updates

#### Page Logic
**Purpose:** Implement page-specific functionality

- **booking.js** - Booking flow orchestration
- **admin.js** - Admin dashboard features
- **customer.js** - Customer dashboard features
- **groomer.js** - Groomer dashboard features
- **staff.js** - Staff dashboard features

#### Utilities
**Purpose:** Shared utility functions

- **auth.js** - Authentication and authorization
- **main.js** - Global utilities and helpers
- **custom-alert.js** - Custom alert component

#### Tests
**Purpose:** Comprehensive test coverage

**Unit Tests:**
- `booking-state.test.js` - State manager tests
- `booking-logic.test.js` - Business logic tests
- `booking-ui.test.js` - UI rendering tests
- `booking-events.test.js` - Event system tests
- `modal-system.test.js` - Modal system tests
- `booking-form-input.test.js` - Form input tests
- `booking-form-input-integration.test.js` - Form integration tests

**Property-Based Tests:**
- `booking-state.pbt.js` - State properties (100+ test cases)
- `booking-logic.pbt.js` - Logic properties (150+ test cases)
- `booking-events.pbt.js` - Event properties (100+ test cases)

**Integration Tests:**
- `booking-consolidation.test.js` - Consolidation tests
- `booking-integration-example.js` - Integration examples

---

### `/css` - Stylesheets
**Purpose:** All styling for the application
**Organization:** One file per page/component

- `styles.css` - Global styles (colors, fonts, spacing)
- `components.css` - Reusable component styles
- `booking.css` - Booking page specific styles
- `admin-dashboard.css` - Admin dashboard styles
- `customer-dashboard.css` - Customer dashboard styles
- `groomer-dashboard.css` - Groomer dashboard styles
- `staff-dashboard.css` - Staff dashboard styles
- `login.css` - Login page styles
- `signup.css` - Signup page styles
- `policy.css` - Policy page styles
- `index.css` - Home page styles
- `custom-alert.css` - Alert component styles

---

### `/assets` - Media Files
**Purpose:** Images and other media resources

- `logo.png` - Company logo
- `1.jpg - 8.jpg` - Gallery images
- `pics.jpg` - Additional images

---

### `/doc` - Documentation
**Purpose:** Project documentation and guides

- `CONSOLIDATION_TEST_GUIDE.md` - Testing guide

---

### `/scripts` - Utility Scripts
**Purpose:** One-off scripts for data management

- `dedupe-booking.js` - Data deduplication script

---

### Root Level - Dashboard Pages
**Purpose:** Main application pages (require authentication)

- `booking.html` - Booking flow page
- `booking-success.html` - Booking confirmation page
- `admin-dashboard.html` - Admin interface
- `customer-dashboard.html` - Customer interface
- `groomer-dashboard.html` - Groomer interface
- `groomer-setup-tool.html` - Groomer setup tool
- `fix-groomer-roles.html` - Admin tool for role management
- `pbt-runner.html` - Property-based test runner
- `test-runner.html` - Unit test runner

---

## 🚀 Quick Start for New Developers

### 1. Understanding the Flow
1. User visits `/public/index.html` (home page)
2. User logs in via `/public/login.html`
3. User is redirected to `booking.html` (dashboard)
4. `booking.js` initializes the booking system
5. Core modules handle state, logic, UI, and events
6. Firebase stores and retrieves data

### 2. Adding a New Feature
1. **Create the page:** `new-feature.html` in root or `/public`
2. **Create the logic:** `new-feature.js` in `/js`
3. **Create the styles:** `new-feature.css` in `/css`
4. **Create the tests:** `new-feature.test.js` in `/js`
5. **Import Firebase:** `import { ... } from '../firebase/firebase-db.js'`
6. **Link from navigation:** Add link in relevant HTML files

### 3. Modifying Existing Features
1. **Find the page:** Look in `/public` or root
2. **Find the logic:** Look in `/js/page-name.js`
3. **Find the styles:** Look in `/css/page-name.css`
4. **Find the tests:** Look in `/js/page-name.test.js`
5. **Update all related files**
6. **Run tests:** `npm test`

### 4. Working with Firebase
1. **Add a function:** Edit `/firebase/firebase-db.js`
2. **Import in your page:** `import { newFunction } from '../firebase/firebase-db.js'`
3. **Use in your logic:** Call the function from your page logic
4. **Test it:** Write tests in `/js/page-name.test.js`

## 📝 File Naming Conventions

### HTML Files
- Public pages: `/public/page-name.html`
- Dashboard pages: `page-name.html` (root)
- Examples: `index.html`, `booking.html`, `admin-dashboard.html`

### JavaScript Files
- Page logic: `/js/page-name.js`
- Core modules: `/js/booking-module-name.js`
- Utilities: `/js/utility-name.js`
- Tests: `/js/page-name.test.js`
- PBT tests: `/js/module-name.pbt.js`

### CSS Files
- Page styles: `/css/page-name.css`
- Global styles: `/css/styles.css`
- Component styles: `/css/components.css`

### Firebase Files
- Configuration: `/firebase/firebase-config.js`
- Database: `/firebase/firebase-db.js`

## ✅ Path Checklist

Before committing code, verify:

- [ ] All `<link>` tags use correct relative paths
- [ ] All `<script>` tags use correct relative paths
- [ ] All `<img>` tags use correct relative paths
- [ ] All `import` statements use correct relative paths
- [ ] Public pages use `../` prefix
- [ ] Dashboard pages use direct paths
- [ ] Firebase imports use `../firebase/`
- [ ] No hardcoded absolute paths

## 🔗 Common Import Patterns

### From Public Pages
```html
<!-- CSS -->
<link rel="stylesheet" href="../css/styles.css">

<!-- Firebase -->
<script type="module" src="../firebase/firebase-config.js"></script>
<script type="module" src="../firebase/firebase-db.js"></script>

<!-- JavaScript -->
<script src="../js/main.js"></script>
<script src="../js/auth.js"></script>
```

### From Dashboard Pages
```html
<!-- CSS -->
<link rel="stylesheet" href="css/styles.css">

<!-- Firebase -->
<script type="module" src="firebase/firebase-config.js"></script>
<script type="module" src="firebase/firebase-db.js"></script>

<!-- JavaScript -->
<script src="js/main.js"></script>
<script src="js/booking.js"></script>
```

### From JavaScript Files
```javascript
// Import from Firebase
import { getBookings, saveBooking } from '../firebase/firebase-db.js';

// Import from other JS files
import { BookingStateManager } from './booking-state.js';
import { validatePhoneNumber } from './booking-logic.js';
```

## 📞 Support

For questions about the project structure:
1. Check `PROJECT_STRUCTURE.md` for overview
2. Check `ORGANIZATION_GUIDE.md` (this file) for details
3. Look at existing files for examples
4. Follow the patterns you see in the codebase

---

**Last Updated:** December 2024
**Version:** 1.0
**Status:** ✅ Organized and Ready

