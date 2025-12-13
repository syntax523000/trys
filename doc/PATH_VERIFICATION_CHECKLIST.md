# Path Verification Checklist

## ✅ Verify All File Paths Are Correct

Use this checklist to ensure all import paths and resource links are correct throughout the project.

---

## 📄 Public Pages (`/public/`)

### `/public/index.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

### `/public/login.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

### `/public/signup.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

### `/public/services.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

### `/public/reviews.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

### `/public/policy.html`
- [ ] CSS links use `../css/`
- [ ] Script tags use `../js/` and `../firebase/`
- [ ] Image tags use `../assets/`
- [ ] No hardcoded absolute paths

---

## 📄 Dashboard Pages (root `/`)

### `booking.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] All modules loaded: booking-state.js, booking-logic.js, booking-ui.js, booking-events.js, modal-system.js
- [ ] No hardcoded absolute paths

### `admin-dashboard.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] Modal system loaded: `js/modal-system.js`
- [ ] No hardcoded absolute paths

### `customer-dashboard.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `groomer-dashboard.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `booking-success.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `groomer-setup-tool.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `fix-groomer-roles.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `pbt-runner.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

### `test-runner.html`
- [ ] CSS links use `css/` (no `../`)
- [ ] Script tags use `js/` and `firebase/` (no `../`)
- [ ] Image tags use `assets/` (no `../`)
- [ ] No hardcoded absolute paths

---

## 📄 JavaScript Files (`/js/`)

### Core Modules
- [ ] `booking-state.js` - No imports needed (standalone)
- [ ] `booking-logic.js` - No imports needed (standalone)
- [ ] `booking-ui.js` - No imports needed (standalone)
- [ ] `booking-events.js` - No imports needed (standalone)
- [ ] `modal-system.js` - No imports needed (standalone)
- [ ] `booking-integration.js` - Imports use `./` for local modules

### Page Logic
- [ ] `booking.js` - Firebase imports use `../firebase/firebase-db.js`
- [ ] `admin.js` - Firebase imports use `../firebase/firebase-db.js`
- [ ] `customer.js` - Firebase imports use `../firebase/firebase-db.js`
- [ ] `groomer.js` - Firebase imports use `../firebase/firebase-db.js`
- [ ] `staff.js` - Firebase imports use `../firebase/firebase-db.js`

### Utilities
- [ ] `auth.js` - Firebase imports use `../firebase/firebase-db.js`
- [ ] `main.js` - No imports needed (global utilities)
- [ ] `custom-alert.js` - No imports needed (standalone)

### Tests
- [ ] All test files import modules correctly
- [ ] All test files use correct relative paths
- [ ] No hardcoded absolute paths in tests

---

## 📄 Firebase Files (`/firebase/`)

### `firebase-config.js`
- [ ] No imports needed (configuration only)
- [ ] Exports Firebase instance

### `firebase-db.js`
- [ ] Imports firebase-config.js: `import './firebase-config.js'`
- [ ] Exports all database functions
- [ ] No hardcoded absolute paths

---

## 📄 CSS Files (`/css/`)

### All CSS Files
- [ ] No imports of other CSS files (use `<link>` in HTML instead)
- [ ] No hardcoded absolute paths
- [ ] No references to external resources with absolute paths

---

## 🔍 Verification Steps

### Step 1: Check All HTML Files
```bash
# Look for incorrect paths in HTML files
grep -r "src=\"/" test-main/*.html
grep -r "href=\"/" test-main/*.html
grep -r "src=\"js/" test-main/public/*.html
grep -r "href=\"css/" test-main/public/*.html
```

### Step 2: Check All JavaScript Files
```bash
# Look for incorrect imports in JS files
grep -r "from '/" test-main/js/*.js
grep -r "from \"/" test-main/js/*.js
grep -r "import.*firebase" test-main/js/*.js
```

### Step 3: Manual Verification
1. Open each HTML file in browser
2. Check browser console for 404 errors
3. Check network tab for failed requests
4. Verify all resources load correctly

### Step 4: Test All Pages
- [ ] `/public/index.html` loads correctly
- [ ] `/public/login.html` loads correctly
- [ ] `/public/signup.html` loads correctly
- [ ] `/public/services.html` loads correctly
- [ ] `/public/reviews.html` loads correctly
- [ ] `/public/policy.html` loads correctly
- [ ] `booking.html` loads correctly
- [ ] `admin-dashboard.html` loads correctly
- [ ] `customer-dashboard.html` loads correctly
- [ ] `groomer-dashboard.html` loads correctly
- [ ] `booking-success.html` loads correctly
- [ ] `groomer-setup-tool.html` loads correctly
- [ ] `fix-groomer-roles.html` loads correctly
- [ ] `pbt-runner.html` loads correctly
- [ ] `test-runner.html` loads correctly

---

## 🐛 Common Path Issues

### Issue: 404 Error for CSS
**Symptom:** Styles not loading, console shows 404 for CSS
**Solution:** 
- Public pages: Use `../css/filename.css`
- Dashboard pages: Use `css/filename.css`

### Issue: 404 Error for JavaScript
**Symptom:** Scripts not loading, console shows 404 for JS
**Solution:**
- Public pages: Use `../js/filename.js`
- Dashboard pages: Use `js/filename.js`

### Issue: 404 Error for Images
**Symptom:** Images not displaying, console shows 404 for images
**Solution:**
- Public pages: Use `../assets/filename.jpg`
- Dashboard pages: Use `assets/filename.jpg`

### Issue: Firebase Not Connecting
**Symptom:** Database operations fail, console shows errors
**Solution:**
- Check firebase-config.js is loaded
- Check firebase-db.js is loaded
- Verify paths: `../firebase/firebase-config.js` and `../firebase/firebase-db.js`

### Issue: Module Import Errors
**Symptom:** Console shows "Cannot find module" or "Failed to import"
**Solution:**
- Check import path uses `../firebase/` for Firebase
- Check import path uses `./` for local modules
- Verify file extension `.js` is included
- Verify file exists at the specified path

---

## ✅ Final Checklist

Before deploying, verify:

- [ ] All public pages use `../` for resources
- [ ] All dashboard pages use direct paths (no `../`)
- [ ] All JavaScript imports use correct relative paths
- [ ] All Firebase imports use `../firebase/`
- [ ] No hardcoded absolute paths anywhere
- [ ] All 404 errors resolved
- [ ] All pages load without console errors
- [ ] All tests pass
- [ ] All resources load correctly

---

## 📝 Path Reference Table

| File Location | CSS Path | JS Path | Firebase Path | Assets Path |
|---------------|----------|---------|---------------|-------------|
| `/public/*.html` | `../css/` | `../js/` | `../firebase/` | `../assets/` |
| `/*.html` (root) | `css/` | `js/` | `firebase/` | `assets/` |
| `/js/*.js` | N/A | `./` | `../firebase/` | N/A |
| `/firebase/*.js` | N/A | N/A | `./` | N/A |

---

## 🚀 Deployment Checklist

Before deploying to production:

- [ ] Run path verification script
- [ ] Check all pages load without errors
- [ ] Check all resources load correctly
- [ ] Run all tests
- [ ] Check browser console for warnings
- [ ] Check network tab for failed requests
- [ ] Test on different browsers
- [ ] Test on mobile devices
- [ ] Verify Firebase connection
- [ ] Verify all features work correctly

---

**Last Updated:** December 2024
**Status:** ✅ Ready for Verification

