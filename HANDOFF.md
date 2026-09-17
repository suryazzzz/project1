# 📋 SRITHI THE COUTURE — Developer Handoff Document

> **Copy and paste this document when handing off to another developer, AI agent, or when resuming work in a new session.**

---

## 1. PROJECT IDENTITY
- **Brand Name**: SRITHI THE COUTURE *(Always uppercase)*
- **Tagline**: Elegant Ethnic Wear
- **Contact**: `+91 89403 77744` / `+91 89403 77733`
- **Type**: Premium Indian Ethnic Fashion E-Commerce
- **Scope**: Exclusively **Sarees** and **Salwar Suits** — *NO other categories (no Western wear, kurtis, kids wear, jewelry, etc.)*

---

## 2. WHAT HAS BEEN BUILT
- **Main Entry Point**: `index.html` in this directory
- **Tech Stack**:
  - React 18 via CDN (`unpkg.com`)
  - Babel Standalone for in-browser JSX transpilation
  - Tailwind CSS via CDN (with custom theme config)
  - Google Fonts: `Playfair Display` (headings) + `Lato` (body)
  - Product images: Unsplash public CDN (consistent 4:5 portrait ratio)
  - Routing: Hash-based SPA routing (`window.location.hash`)
  - State: React root state hooks (`useState`, `useCallback`, `useMemo`)
- **File Size**: ~91 KB (~1,730 lines of clean code)

---

## 3. DESIGN SYSTEM
### Color Palette
- `cream`: `#FAF7F2` (Primary page background)
- `ivory`: `#F5F0E8` (Secondary background, alternating sections)
- `maroon`: `#6B1A2A` (Primary brand color, CTAs, active states)
- `burgundy`: `#8B2139` (Hover states, limited stock badge)
- `gold`: `#C9972A` (Accent color, borders, icons, price text)
- `gold-light`: `#E8B84B` (Gradient end, discount badges)
- `beige`: `#D4C5A9` (Dividers, borders)
- `dark-brown`: `#2C1A0E` (Primary typography, dark footer background)
- `warm-gray`: `#8B7D72` (Secondary text, placeholders)

### Typography
- **Headings & Product Titles**: `Playfair Display` (serif)
- **Body, Buttons & UI**: `Lato` (sans-serif)

### Button & Badge System
- `.btn-gold`: Gradient gold background, dark-brown text
- `.btn-maroon`: Solid maroon background, cream text
- `.btn-outline`: Transparent background, gold border, maroon text
- `.badge-new`: Gold background
- `.badge-best`: Maroon background
- `.badge-sale`: Light gold background, dark-brown text
- `.badge-limited`: Burgundy background
- **Image Aspect Ratio**: 4:5 portrait (`.aspect-product`)

---

## 4. COMPONENT ARCHITECTURE
```
App
├── Header (Logo, Desktop Nav, Search Bar Toggle, Icons: Search/Wishlist/Cart/User, Mobile Menu)
├── Hash Router
│   ├── #/                  → HomePage (HeroBanner, CategorySection, New Arrivals, Best Sellers, Previews, Offers, WhyShop, Reviews)
│   ├── #/sarees            → ProductListingPage (category="Sarees", FilterPanel, SortDropdown, ProductGrid)
│   ├── #/salwars           → ProductListingPage (category="Salwars", FilterPanel, SortDropdown, ProductGrid)
│   ├── #/new-arrivals      → FilteredPage (filter="new")
│   ├── #/best-sellers      → FilteredPage (filter="best")
│   ├── #/offers            → FilteredPage (filter="offers")
│   ├── #/product/:id       → ProductDetailsPage (Gallery, Specs, SizeSelector, Cart/Buy, Reviews)
│   ├── #/cart              → CartPage (Item list, price breakdown, promo, checkout CTA)
│   ├── #/checkout          → CheckoutPage (Address form, payment method, order summary)
│   ├── #/wishlist          → WishlistPage (Saved items grid)
│   ├── #/search            → SearchPage (Multi-field query search)
│   └── #/size-guide        → SizeGuidePage (Salwar sizing chart modal/page)
├── Footer (Newsletter, Navigation Links, Socials, Policy)
└── Toast Notifications (Bottom-right, 2.4s auto-dismiss)
```

---

## 5. BUSINESS LOGIC & CONSTRAINTS
1. **Category Constraint**: Strictly Sarees & Salwars only.
2. **Currency**: All prices in Indian Rupee (`₹`), formatted with Indian comma system (`en-IN`).
3. **Delivery Fee**: Orders ≥ ₹999 get free shipping; orders below ₹999 incur ₹79.
4. **Cart Key**: `${id}-${size}` to distinguish different size lines for the same Salwar product.
5. **Size Validation**: Adding Salwars to cart or proceeding to checkout requires selecting a size (`S`, `M`, `L`, `XL`, `XXL`).
6. **Image Specifications**: 4:5 portrait aspect ratio, clean backgrounds.

---

## 6. ROADMAP & NEXT PHASES
- **Phase 1**: Migration to Vite + modular React + React Router DOM + Tailwind build
- **Phase 2**: LocalStorage / Context API state persistence
- **Phase 3**: Backend REST API (Node.js/Express or Supabase)
- **Phase 4**: User Authentication & Profiles
- **Phase 5**: Indian Payment Gateway (Razorpay/UPI integration)
- **Phase 6**: Admin Management Dashboard (Products & Orders)
- **Phase 7**: Production image hosting, SEO meta tags, and SSR/SSG
