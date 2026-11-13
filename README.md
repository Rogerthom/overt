# ARCHIVE

An independent reseller of curated pre-owned clothing — editorial storefront, built as a demo.

All inventory, prices, measurements and policies are placeholder content. No real orders are placed and no card details are collected anywhere in the flow.

## Stack

- React 19 + TypeScript + Vite
- Tailwind CSS v4
- react-router
- React Three Fiber (lazy-loaded hero scene, desktop only)
- Hono worker for `/api/orders` and `/api/newsletter`

## Routes

| Path | Page |
| --- | --- |
| `/` | Home, with the 3D hero |
| `/shop` | Catalogue with brand, category, size, condition and price filters |
| `/product/:slug` | Product detail, measurements and condition notes |
| `/saved` | Saved items |
| `/about` | Buying, condition, shipping and returns guidance |
| `/checkout` | Demo checkout — collects no payment details |
| `/order/:reference` | Demo order confirmation |

## Run locally

```bash
npm install
npm run dev        # http://localhost:5173
npm run build      # builds dist/client and dist/store
npx tsc --noEmit   # typecheck
```

## Editing the catalogue

Every product lives in `src/data/products.ts` — one array, plus `FREE_SHIPPING_AT` and `DEMO_NOTE`. Images currently point at `public/images/placeholder-01..06.svg`; replace those files with real photography of the same filenames.

## Notes

- Demo checkout stops at a reference number. Wiring a real payment provider means replacing the `POST /api/orders` handler and redirecting to a hosted checkout.
- The Hono worker needs a host that runs it (the `deploy.json` in this project targets Cloudflare). Static hosting alone will not serve `/api/*`.
