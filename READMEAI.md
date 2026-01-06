You are a senior full-stack engineer building a production-ready local service website template in a GitHub repo (developed in GitHub Codespaces).

GOAL
Build “Archetype 8 — Local Food / Hospitality (menu + discovery)” as a reusable, modern, high-converting marketing template for restaurants, coffee shops, quick service, and catering.

Primary conversions:
- Visit (hours/location/directions)
- Order Online (takeout/delivery)
- Reservations (if applicable)
Secondary conversion:
- Catering inquiries (separate funnel)

STACK (REQUIRED)
- Next.js (App Router)
- TypeScript
- Tailwind CSS
No CMS. No database. Single config file for all content + behavior.

MARKETING + DISCOVERY STANDARDS FOR THIS ARCHETYPE (NON-NEGOTIABLE)
A) Menu must be mobile-first and indexable (NOT a PDF)
- Implement /menu as a real page with sections/items (config-driven).
- Menu must be easy to scroll and tap on mobile; CTA buttons visible without hunting.
Restaurant website guidance repeatedly emphasizes mobile-friendly menus and visible CTAs. :contentReference[oaicite:4]{index=4}

B) Location + hours must be unmissable
- Home page above fold must show:
  - Today’s hours (or open/closed status)
  - Address + directions link
  - Phone (tap-to-call)
Accurate hours and location info are critical for restaurants and directly affect visits/orders. :contentReference[oaicite:5]{index=5}

C) Ordering/reservations as primary CTAs (config-driven)
- Sticky primary CTA is either:
  - “Order Online” OR “Reserve” (config selects)
- Secondary CTA is the other (if enabled), else “Call”.

D) Catering must be its own funnel
- /catering page:
  - packages or request form
  - response time expectations (TODO:INPUT)
  - separate CTA: “Request Catering Quote”

E) GBP/Discovery readiness
- Site must support NAP consistency + LocalBusiness structured data.
Google’s LocalBusiness structured data helps communicate hours/location and may enhance search results. :contentReference[oaicite:6]{index=6}
- Do not attempt to “edit GBP” from the website, but include an internal note in README: keep GBP menu/hours accurate (GBP has menu management features). :contentReference[oaicite:7]{index=7}

OUTPUT CONTRACT (ANTI-TRUNCATION)
You MUST deliver the repo in STAGES. Do NOT omit code “for brevity”.
Stage A: Repo scaffold + config + layout + libs + SEO endpoints + devcontainer + tooling.
Stage B: Components/sections + pages/routes (Home, Menu, Order, Reservations, Catering, About, Gallery, Reviews, Contact, Policies, Privacy, Terms, 404).
Stage C: QA checklist + README + final notes (build/lint/dev).

If you reach output limits mid-stage, STOP and print: “STOPPED AT: <filepath>”.

QUALITY BAR (MUST PASS)
- npm run dev
- npm run build
- npm run lint
- No runtime errors.
- No lorem ipsum. Unknown inputs must be explicit: "TODO:INPUT".

CODE COMMENTARY (FOR AI ITERATION)
- Add concise comments:
  - 1–2 line header per file: purpose.
  - Short “why” comments for non-obvious logic.
  - TODOs must be explicit: TODO:INPUT or TODO:PROD.
- Do not add excessive commentary.

NON-NEGOTIABLE UX RULES
- Mobile-first.
- Sticky CTA sitewide via layout:
  - Primary: Order Online OR Reserve (based on config.primaryCtaMode)
  - Secondary: Call (tel:) or the other CTA if enabled
- Add global bottom padding so sticky bar never covers content.
- Header must always include: Menu, Location/Hours (anchor or section), Order/Reserve (if enabled), Catering (if enabled).

MODERN DESIGN ACCEPTANCE CRITERIA (STRICT)
- Consistent container + section spacing rhythm (py-12/py-16).
- Typography hierarchy: hero 3xl–5xl, readable body.
- Buttons: primary + secondary with hover + focus-visible.
- Cards: consistent radius + subtle border/shadow.
- Menu page must be optimized for scanning (section headers, item cards, clear prices).

HOMEPAGE STRUCTURE (ORDER IS MANDATORY)
1) RestaurantHeroSection
   - Headline + subheadline
   - Primary CTA (Order or Reserve)
   - Secondary CTA (Reserve/Order or Call)
   - Above-fold “Visit info” block: Today’s hours + address + directions + tap-to-call
2) MenuHighlightsSection
   - 6–12 featured items (config-driven)
3) SocialProofSection
   - reviews highlights + review platform links
4) AboutBlurbSection
   - short story/positioning
5) GalleryPreviewSection
   - 6 images (placeholders ok)
6) CateringPromoSection (if enabled)
   - CTA to /catering
7) FAQSection
   - 3–6 FAQs (parking, dietary, reservations, delivery radius)
8) CTASection
   - repeat primary CTA

CANONICAL FILE TREE (MUST MATCH EXACTLY)
- src/
  - app/
    - layout.tsx
    - globals.css
    - page.tsx                          (Home)
    - menu/page.tsx
    - order/page.tsx                    (Order Online landing: provider embed/link)
    - reservations/page.tsx             (Reservations landing: provider embed/link)
    - catering/page.tsx
    - about/page.tsx
    - gallery/page.tsx
    - reviews/page.tsx
    - contact/page.tsx
    - policies/page.tsx
    - privacy/page.tsx
    - terms/page.tsx
    - not-found.tsx
    - api/
      - lead/route.ts                   (catering inquiries)
    - robots.ts
    - sitemap.ts
  - components/
    - Header.tsx
    - Footer.tsx
    - StickyCTA.tsx
    - JsonLd.tsx
    - NAP.tsx
    - HoursStatus.tsx                   (open/closed + today hours)
    - ContactMethods.tsx
    - MenuSection.tsx
    - MenuItemCard.tsx
    - ProviderEmbed.tsx                 (order/reservations embed/link)
    - CateringForm.tsx
    - ProofStack.tsx
    - Testimonials.tsx
    - FAQ.tsx
    - sections/
      - RestaurantHeroSection.tsx
      - MenuHighlightsSection.tsx
      - SocialProofSection.tsx
      - AboutBlurbSection.tsx
      - GalleryPreviewSection.tsx
      - CateringPromoSection.tsx
      - FAQSection.tsx
      - CTASection.tsx
  - config/site.ts
  - lib/
    - tracking.ts
    - analytics.ts
    - schema.ts
    - seo.ts
    - rateLimit.ts
    - utils.ts
- public/
  - gallery/
    - 01.jpg
    - 02.jpg
    - 03.jpg
    - 04.jpg
    - 05.jpg
    - 06.jpg
- .devcontainer/devcontainer.json
- README.md
- package.json
- tailwind.config.ts
- postcss.config.js
- tsconfig.json
- eslint config

CONFIG (SINGLE SOURCE OF TRUTH) — EXACT TYPES REQUIRED
In src/config/site.ts define and export these EXACT interfaces and config object. Do not rename fields.

type AnalyticsConfig =
  | { provider: "none" }
  | { provider: "ga4"; ga4MeasurementId: string }
  | { provider: "plausible"; plausibleDomain: string };

type SpamProtectionConfig = {
  turnstileEnabled: boolean;
  turnstileSiteKey?: string;
  turnstileSecretKey?: string;
};

type ProviderMode =
  | { mode: "none" }
  | { mode: "iframe"; iframeUrl: string }
  | { mode: "script"; scriptSrc: string; scriptContainerId: string }
  | { mode: "link"; linkUrl: string; linkLabel?: string };

type PrimaryCtaMode = "order" | "reservations" | "call";

type HoursConfig = {
  timezoneIana: string; // TODO:INPUT (e.g., America/Chicago)
  weekly: { day: "Mon"|"Tue"|"Wed"|"Thu"|"Fri"|"Sat"|"Sun"; open: string; close: string; closed?: boolean }[];
  notes?: string;       // holiday note (do not implement full holiday calendar unless provided)
};

type MenuItem = {
  id: string;
  name: string;
  description?: string;
  price?: string;       // e.g., “$12” or “Market”
  tags?: string[];      // e.g., “Vegan”, “Gluten-free”
  imagePath?: string;
};

type MenuSectionConfig = {
  id: string;
  title: string;
  description?: string;
  items: MenuItem[];
};

type CateringPackage = {
  id: string;
  name: string;
  servesText?: string;  // TODO:INPUT
  priceText?: string;   // TODO:INPUT
  includedBullets: string[];
};

type CateringFormField =
  | { name: "name"; label: string; type: "text"; required: true }
  | { name: "email"; label: string; type: "email"; required: true }
  | { name: "phone"; label: string; type: "tel"; required?: boolean }
  | { name: "eventDate"; label: string; type: "text"; required?: boolean }
  | { name: "guestCount"; label: string; type: "text"; required?: boolean }
  | { name: "budget"; label: string; type: "select"; required?: boolean; options: string[] }
  | { name: "message"; label: string; type: "textarea"; required: true };

type CateringConfig = {
  enabled: boolean;
  packages: CateringPackage[];
  form: {
    fields: CateringFormField[];
    confirmationHeadline: string;
    confirmationBody: string;
  };
};

type CopyBlocks = {
  heroHeadline: string;
  heroSubheadline: string;
  heroBullets: [string, string, string];
  ctaSectionHeadline: string;
  ctaSectionSubheadline: string;
};

export interface SiteConfig {
  baseUrl: string;                // TODO:INPUT
  businessName: string;
  tagline: string;

  primaryCtaMode: PrimaryCtaMode;

  phoneDisplay: string;
  phoneDial: string;
  email?: string;

  address: { line1: string; line2?: string; city: string; state: string; zip: string };
  directionsUrl: string;          // TODO:INPUT

  hours: HoursConfig;

  copy: CopyBlocks;

  menu: {
    sections: MenuSectionConfig[];
    featuredItemIds: string[];    // controls MenuHighlightsSection
  };

  orderOnline: ProviderMode;       // /order behavior
  reservations: ProviderMode;      // /reservations behavior

  catering: CateringConfig;

  galleryImagePaths: string[];     // must be 6 items

  reviews: { highlightQuotes: { name?: string; text: string }[]; reviewPlatformLinks: { label: string; url: string }[] };
  faqs: { q: string; a: string }[];

  leadRouting: { webhookUrl?: string }; // for catering inquiries (TODO:INPUT)
  seo: { siteTitle: string; titleTemplate: string; metaDescription: string; primaryKeywords: string[]; ogImagePath?: string };

  analytics: AnalyticsConfig;
  spamProtection: SpamProtectionConfig;
}

export const siteConfig: SiteConfig = { ... } // populate with TODO:INPUT placeholders

ORDER / RESERVATIONS (DETERMINISTIC)
- ProviderEmbed component:
  - iframe mode: render iframe; fire provider_loaded event
  - script mode: load script only on that page; fire provider_loaded after load
  - link mode: prominent button opens new tab
- /order and /reservations must each have:
  - above-fold CTA
  - fallback “Call to order / reserve” block
Visible CTAs and mobile friendliness are common restaurant best practices. :contentReference[oaicite:8]{index=8}

HOURS STATUS (DETERMINISTIC, NO GUESSING)
- HoursStatus.tsx:
  - compute open/closed based on config.hours.weekly + timezoneIana
  - display “Open now” / “Closed” and today’s hours
Accuracy of hours/location is critical for restaurants. :contentReference[oaicite:9]{index=9}

CATERING LEAD ROUTING + SPAM HARDENING
- CateringForm posts to /api/lead.
- /api/lead must:
  - honeypot + reject if filled
  - best-effort in-memory rate limiting per IP (TODO:PROD seam)
  - sanitize inputs
  - verify Turnstile if enabled + secret provided
  - forward to leadRouting.webhookUrl if present; else console.log and return success

ANALYTICS (STRICT)
- Standard events:
  cta_primary_click, order_click, reservations_click, phone_click, directions_click, menu_view, provider_loaded, catering_submit, catering_success, catering_error
- If GA4 selected: use @next/third-parties/google GoogleAnalytics in layout. :contentReference[oaicite:10]{index=10}
- track() logs to console and forwards to provider if enabled.

SEO RULES (STRICT)
- Canonical URLs via Metadata API: alternates.canonical.
- robots.ts must include Sitemap: `${baseUrl}/sitemap.xml`.
- sitemap.ts must include:
  - /, /menu, /order, /reservations, /catering, /about, /gallery, /reviews, /contact, /policies, /privacy, /terms
- Implement LocalBusiness JSON-LD (Restaurant type acceptable) including hours/address/telephone where applicable. :contentReference[oaicite:11]{index=11}

README REQUIREMENTS
- Explain:
  - how to update menu/hours in config
  - ordering/reservations provider modes
  - catering funnel + webhook integration
  - reminder: keep GBP hours/menu accurate (GBP supports menu management) :contentReference[oaicite:12]{index=12}

NOW EXECUTE STAGE A, then STAGE B, then STAGE C in the same response if possible.
