# Radharani Pharmacy

## Current State
Reviews are stored in browser localStorage, so each user only sees their own submitted reviews. The ReviewsPage.tsx loads/saves reviews from localStorage. The backend has no review-related APIs.

## Requested Changes (Diff)

### Add
- Backend: `Review` type with id, name, rating, comment, createdAt fields
- Backend: `addReview(review)` shared function -> returns Nat ID
- Backend: `getReviews()` query function -> returns all user-submitted reviews
- Frontend: Static seeded reviews data file (~1500+ pre-verified authentic-looking Bengali/Indian reviews with mixed Hindu & Muslim names, Verified Customer badge, realistic dates)
- Frontend: ReviewsPage now loads both seeded reviews + backend reviews, combined and sorted by date
- Frontend: New review submissions go to backend canister (shared across all users, instant)

### Modify
- ReviewsPage.tsx: Replace localStorage logic with backend API calls + seeded static data merge
- backend.d.ts: Add Review type, addReview, getReviews to interface
- main.mo: Add review storage, addReview, getReviews functions

### Remove
- localStorage review read/write from ReviewsPage (STORAGE_KEY, loadReviews, saveReviews functions)

## Implementation Plan
1. Update main.mo with Review type and review CRUD (addReview, getReviews)
2. Generate seededReviews.ts with 1500+ realistic Bengal/India reviews
3. Update ReviewsPage.tsx to call backend.getReviews() + merge with seeded data, submit via backend.addReview()
4. Update backend.d.ts types
5. Validate and build
