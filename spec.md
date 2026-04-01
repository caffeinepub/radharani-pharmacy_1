# Radharani Pharmacy

## Current State
- React SPA with custom router (window.history.pushState)
- Pages: `/` (HomePage), `/admin` (AdminLogin), `/admin/dashboard` (AdminDashboard)
- Header with logo (Cross icon + text), desktop nav, hamburger mobile menu
- DoctorsSection renders 9 doctors from context in a responsive grid
- AppContext provides doctors, settings, inquiries via localStorage + backend
- Logo file: `/assets/uploads/file_00000000ad6472089268d8e963321139-019d3940-a8ef-76c9-80a9-d44a04b6bc15-1.png` (old)
- New logo uploaded: `/assets/1000140718-019d49d7-9b4a-770b-9ad2-98d53769fbb0.png` (green R+cross)
- Favicon in index.html points to old logo

## Requested Changes (Diff)

### Add
- Reviews page at `/reviews` route with public star + name + text review posting, localStorage persistence
- AI-powered sentiment summary badge on reviews page (calculates % positive from stored ratings)
- Health tips animated ticker in Header below nav
- Particle/ambient background on Hero section (CSS-only or canvas, no new deps)
- Review cards with animated star fill entrance and shimmer skeleton loading state
- Magnetic hover micro-interaction on main CTA buttons
- "Reviews" link in header nav (both desktop and mobile)

### Modify
- **index.html**: Update favicon href to `/assets/1000140718-019d49d7-9b4a-770b-9ad2-98d53769fbb0.png`
- **Header.tsx**: Replace Cross icon logo with `<img>` tag using new logo path. Fix mobile nav link bug — use `requestAnimationFrame` or `setTimeout(0)` after `setMobileOpen(false)` to ensure scroll fires after menu collapse. Add Reviews nav link.
- **App.tsx**: Add `/reviews` route handler
- **DoctorsSection.tsx**: Ensure grid is `grid-cols-1 sm:grid-cols-2 lg:grid-cols-3` and all 9 cards render without cutoff. Verify no max-height or overflow hidden issues on container.

### Remove
- Nothing removed

## Implementation Plan
1. Update `index.html` favicon to new logo
2. Update `Header.tsx`: new logo img, fix mobile scroll bug (setTimeout after closing menu), add Reviews nav link
3. Update `App.tsx`: add `/reviews` route
4. Create `src/frontend/src/pages/ReviewsPage.tsx`: full page with public review form (name + stars + comment), review list with animations, AI sentiment badge, shimmer skeleton
5. Fix `DoctorsSection.tsx` if any overflow/container issues found
6. Add health tips ticker to Header
7. Validate and deploy
