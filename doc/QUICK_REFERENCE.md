# BestBuddies Pet Grooming - Quick Reference Card

## 🗂️ Project Structure at a Glance

```
test-main/
├── public/              → Public pages (index, login, signup, etc.)
├── firebase/            → Firebase config & database operations
├── js/                  → All JavaScript (logic, tests, utilities)
├── css/                 → All stylesheets
├── assets/              → Images and media
├── doc/                 → Documentation
├── scripts/             → Utility scripts
└── *.html               → Dashboard pages (booking, admin, etc.)
```

## 📍 Where to Find Things

| What | Where |
|------|-------|
| Home page | `/public/index.html` |
| Login page | `/public/login.html` |
| Signup page | `/public/signup.html` |
| Booking page | `booking.html` |
| Admin dashboard | `admin-dashboard.html` |
| Customer dashboard | `customer-dashboard.html` |
| Groomer dashboard | `groomer-dashboard.html` |
| Firebase config | `/firebase/firebase-config.js` |
| Database functions | `/firebase/firebase-db.js` |
| Booking logic | `/js/booking.js` |
| Admin logic | `/js/admin.js` |
| State manager | `/js/booking-state.js` |
| Business logic | `/js/booking-logic.js` |
| UI rendering | `/js/booking-ui.js` |
| Event system | `/js/booking-events.js` |
| Modal system | `/js/modal-system.js` |
| Global styles | `/css/styles.css` |
| Component styles | `/css/components.css` |
| Booking styles | `/css/booking.css` |
| Logo | `/assets/logo.png` |

## 🔗 Import Paths Quick Guide

### From `/public/` pages
```html
<link rel="stylesheet" href="../css/styles.css">
<script src="../js/main.js"></script>
<script src="../firebase/firebase-config.js"></script>
<img src="../assets/logo.png">
```

### From root pages (booking.html, admin-dashboard.html, etc.)
```html
<link rel="stylesheet" href="css/styles.css">
<script src="js/main.js"></script>
<script src="firebase/firebase-config.js"></script>
<img src="assets/logo.png">
```

### From `/js/` files
```javascript
import { getBookings } from '../firebase/firebase-db.js';
import { BookingStateManager } from './booking-state.js';
```

## 🧪 Testing

### Run Unit Tests
```bash
npm test -- js/booking-state.test.js
npm test -- js/booking-logic.test.js
npm test -- js/booking-ui.test.js
```

### Run Property-Based Tests
Open in browser: `pbt-runner.html`

### Run All Tests
```bash
npm test
```

## 📝 Common Tasks

### Add a New Public Page
1. Create `/public/new-page.html`
2. Use `../` for all resource paths
3. Link from `/public/index.html`

### Add a New Dashboard Page
1. Create `new-dashboard.html` in root
2. Use direct paths (no `../`)
3. Create `/js/new-dashboard.js` for logic
4. Create `/css/new-dashboard.css` for styles

### Add a New Firebase Function
1. Edit `/firebase/firebase-db.js`
2. Add your function
3. Export it: `export function myFunction() { ... }`
4. Import in your page: `import { myFunction } from '../firebase/firebase-db.js'`

### Add a New Test
1. Create `/js/feature-name.test.js`
2. Write unit tests
3. Run: `npm test -- js/feature-name.test.js`

### Add a New Style
1. Create `/css/feature-name.css`
2. Link in HTML: `<link rel="stylesheet" href="css/feature-name.css">`
3. Or add to existing CSS file

## 🚀 Development Workflow

1. **Start development server**
   ```bash
   npm run dev
   ```

2. **Make changes** to HTML, JS, or CSS

3. **Test your changes**
   ```bash
   npm test
   ```

4. **Commit your changes**
   ```bash
   git add .
   git commit -m "Description of changes"
   ```

5. **Push to repository**
   ```bash
   git push
   ```

## 🐛 Debugging Tips

### Check Console Errors
1. Open browser DevTools (F12)
2. Go to Console tab
3. Look for red error messages
4. Check the file path in the error

### Check Network Requests
1. Open browser DevTools (F12)
2. Go to Network tab
3. Look for failed requests (red)
4. Check the URL path

### Check Firebase Connection
1. Open browser DevTools (F12)
2. Go to Console tab
3. Type: `firebase.database().ref().once('value')`
4. Should return data if connected

## 📚 Documentation Files

| File | Purpose |
|------|---------|
| `PROJECT_STRUCTURE.md` | Overview of folder structure |
| `ORGANIZATION_GUIDE.md` | Detailed organization guide |
| `QUICK_REFERENCE.md` | This file - quick lookup |
| `/firebase/FIREBASE_SETUP_INSTRUCTIONS.md` | Firebase setup guide |
| `/doc/CONSOLIDATION_TEST_GUIDE.md` | Testing guide |

## ⚠️ Common Mistakes

### ❌ Wrong Path in Public Page
```html
<!-- WRONG -->
<script src="js/main.js"></script>

<!-- RIGHT -->
<script src="../js/main.js"></script>
```

### ❌ Wrong Path in Dashboard Page
```html
<!-- WRONG -->
<script src="../js/main.js"></script>

<!-- RIGHT -->
<script src="js/main.js"></script>
```

### ❌ Hardcoded Absolute Path
```javascript
// WRONG
import { getBookings } from '/firebase/firebase-db.js';

// RIGHT
import { getBookings } from '../firebase/firebase-db.js';
```

### ❌ Missing File Extension
```javascript
// WRONG
import { getBookings } from '../firebase/firebase-db';

// RIGHT
import { getBookings } from '../firebase/firebase-db.js';
```

## 🎯 Key Principles

1. **Always use relative paths** - Makes code portable
2. **Public pages use `../`** - They're in a subfolder
3. **Dashboard pages use direct paths** - They're in root
4. **Keep modules small** - One responsibility per file
5. **Write tests** - Every new function needs tests
6. **Escape user input** - Prevent XSS attacks
7. **Use state manager** - Don't mutate global state
8. **Follow patterns** - Look at existing code for examples

## 📞 Need Help?

1. Check the relevant documentation file
2. Look at similar existing code
3. Check the browser console for errors
4. Check the network tab for failed requests
5. Ask a team member

---

**Quick Links:**
- 📖 Full Structure: `PROJECT_STRUCTURE.md`
- 📋 Detailed Guide: `ORGANIZATION_GUIDE.md`
- 🔧 Firebase Setup: `/firebase/FIREBASE_SETUP_INSTRUCTIONS.md`
- 🧪 Testing Guide: `/doc/CONSOLIDATION_TEST_GUIDE.md`

