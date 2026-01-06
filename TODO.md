# TODO - Food / Hospitality Template

## Stage A: Repo Scaffold + Config + Layout + Libs + SEO Endpoints + DevContainer + Tooling

- [ ] Initialize Next.js project with App Router
- [ ] Configure TypeScript
- [ ] Set up Tailwind CSS
- [ ] Create single config file (`src/config/site.ts`) with all type definitions
- [ ] Create layout (`src/app/layout.tsx`)
- [ ] Create `src/app/globals.css`
- [ ] Set up SEO endpoints:
  - [ ] `src/app/robots.ts`
  - [ ] `src/app/sitemap.ts`
- [ ] Create `.devcontainer/devcontainer.json`
- [ ] Configure tooling:
  - [ ] `package.json`
  - [ ] `tailwind.config.ts`
  - [ ] `postcss.config.js`
  - [ ] `tsconfig.json`
  - [ ] ESLint config
- [ ] Create lib files:
  - [ ] `src/lib/tracking.ts`
  - [ ] `src/lib/analytics.ts`
  - [ ] `src/lib/schema.ts`
  - [ ] `src/lib/seo.ts`
  - [ ] `src/lib/rateLimit.ts`
  - [ ] `src/lib/utils.ts`

## Stage B: Components/Sections + Pages/Routes

### Components

- [ ] `src/components/Header.tsx`
- [ ] `src/components/Footer.tsx`
- [ ] `src/components/StickyCTA.tsx`
- [ ] `src/components/JsonLd.tsx`
- [ ] `src/components/NAP.tsx`
- [ ] `src/components/HoursStatus.tsx` (open/closed + today hours)
- [ ] `src/components/ContactMethods.tsx`
- [ ] `src/components/MenuSection.tsx`
- [ ] `src/components/MenuItemCard.tsx`
- [ ] `src/components/ProviderEmbed.tsx` (order/reservations embed/link)
- [ ] `src/components/CateringForm.tsx`
- [ ] `src/components/ProofStack.tsx`
- [ ] `src/components/Testimonials.tsx`
- [ ] `src/components/FAQ.tsx`

### Section Components

- [ ] `src/components/sections/RestaurantHeroSection.tsx`
- [ ] `src/components/sections/MenuHighlightsSection.tsx`
- [ ] `src/components/sections/SocialProofSection.tsx`
- [ ] `src/components/sections/AboutBlurbSection.tsx`
- [ ] `src/components/sections/GalleryPreviewSection.tsx`
- [ ] `src/components/sections/CateringPromoSection.tsx`
- [ ] `src/components/sections/FAQSection.tsx`
- [ ] `src/components/sections/CTASection.tsx`

### Pages

- [ ] `src/app/page.tsx` (Home)
- [ ] `src/app/menu/page.tsx`
- [ ] `src/app/order/page.tsx` (Order Online landing)
- [ ] `src/app/reservations/page.tsx` (Reservations landing)
- [ ] `src/app/catering/page.tsx`
- [ ] `src/app/about/page.tsx`
- [ ] `src/app/gallery/page.tsx`
- [ ] `src/app/reviews/page.tsx`
- [ ] `src/app/contact/page.tsx`
- [ ] `src/app/policies/page.tsx`
- [ ] `src/app/privacy/page.tsx`
- [ ] `src/app/terms/page.tsx`
- [ ] `src/app/not-found.tsx`

### API Routes

- [ ] `src/app/api/lead/route.ts` (catering inquiries)

### Public Assets

- [ ] `public/gallery/01.jpg`
- [ ] `public/gallery/02.jpg`
- [ ] `public/gallery/03.jpg`
- [ ] `public/gallery/04.jpg`
- [ ] `public/gallery/05.jpg`
- [ ] `public/gallery/06.jpg`

## Stage C: QA Checklist + README + Final Notes

### QA Checklist

- [ ] `npm run dev` works without errors
- [ ] `npm run build` completes successfully
- [ ] `npm run lint` passes
- [ ] No runtime errors
- [ ] No lorem ipsum (use "TODO:INPUT" for unknown inputs)
- [ ] Mobile-first design verified
- [ ] Sticky CTA visible sitewide
- [ ] Global bottom padding prevents sticky bar overlap

### Documentation

- [ ] Create `README.md` with:
  - [ ] How to update menu/hours in config
  - [ ] Ordering/reservations provider modes explanation
  - [ ] Catering funnel + webhook integration
  - [ ] Reminder: keep GBP hours/menu accurate

---

## TODO:INPUT Items (Require Client Input)

- [ ] `baseUrl` - Production URL
- [ ] `timezoneIana` - Business timezone (e.g., America/Chicago)
- [ ] `directionsUrl` - Google Maps directions link
- [ ] Catering response time expectations
- [ ] Catering package details (`servesText`, `priceText`)
- [ ] `leadRouting.webhookUrl` - Webhook for catering inquiries
- [ ] GA4 Measurement ID (if using GA4 analytics)
- [ ] Plausible domain (if using Plausible analytics)
- [ ] Turnstile site key and secret key (if enabling spam protection)

## TODO:PROD Items (Production Considerations)

- [ ] Implement persistent rate limiting (replace in-memory solution)
- [ ] Set up actual ordering provider integration
- [ ] Set up actual reservations provider integration
- [ ] Replace placeholder gallery images
- [ ] Configure analytics provider
- [ ] Set up catering webhook endpoint
