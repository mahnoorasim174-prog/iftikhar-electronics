# Iftikhar Electronics — Website

Single-page catalog website for **Iftikhar Electronics**, Darya Khan — a solar panel, home appliance and electronics retailer. The site showcases 15 product categories with WhatsApp-based ordering, built as one self-contained HTML file.

---

## Overview

- **Type:** Single-page product catalog (no backend, no database)
- **File:** `index.html` — everything (HTML, CSS, JavaScript, logo) is in this one file
- **Ordering:** Every product has an "Order on WhatsApp" button that opens a pre-filled WhatsApp chat with the product name and price
- **Categories:** 15
- **Products:** 69

---

## Business Information

| Field | Value |
|---|---|
| Business name | Iftikhar Electronics |
| Location | Bhakkar Road, opposite MCB Bank, Darya Khan |
| Phone / WhatsApp | 0346 0642661 |
| Email | iftikhardarya2015@gmail.com |

---

## Product Categories

1. Solar Panels
2. Refrigerators
3. Lithium Batteries
4. Air Coolers
5. Ceiling & Pedestal Fans
6. Microwave Ovens
7. Dry & Steam Irons
8. Inverter Split Air Conditioners
9. Speakers & Media Systems
10. Solar PV Circuit Breakers
11. Electric Bikes
12. Washing Machines
13. LED & Smart TVs
14. Water Motors & Pumps
15. Juicers, Blenders & Kettles

---

## Design System

- **Fonts:** DM Serif Display (headings) + Manrope (body text and buttons), loaded from Google Fonts
- **Brand colors:**
  - Navy (primary): `#0a1f38`
  - Amber (accent): `#f2994a`
  - WhatsApp green: `#25d366`
- **Layout:** Persistent left sidebar for category navigation on desktop; collapses into a top icon bar with a slide-out menu on tablet/mobile
- **Product layouts:** Categories alternate between three card patterns (grid/bento, horizontal scroll rail, and split list) so the page doesn't feel repetitive
- **Logo:** Custom lightning-bolt mark embedded directly in the page as a base64 image (no external logo file needed) — used in the header and footer, outline color matched exactly to the site's amber brand color

---

## How the Site Works

- Clicking a category in the sidebar/menu jumps to that section
- Clicking a product card opens a detail popup with a larger image, description, and quantity selector
- Every "Order on WhatsApp" button opens `https://wa.me/923460642661` with a pre-written message containing the product name and price
- The site is fully responsive: desktop, tablet, and mobile all have their own tested layouts
- No page reload is needed for any interaction — everything (product popup, category menu, WhatsApp links) works with plain JavaScript already built into the file

---

## How to Update Products or Prices

Open `index.html` in any text/code editor and search for the product name you want to change. Each product is one block that looks like this:

```html
<article class="p-card" data-pid="cat-1-1">
  <div class="p-media">
    <span class="p-brand">Astronergy</span>
    <span class="p-stock">In stock</span>
    <img src="IMAGE_URL" alt="..." loading="lazy" />
  </div>
  <div class="p-info">
    <h3 class="p-name">Astronergy 620W N-Type TOPCon Panel</h3>
    <div class="p-divider"></div>
    <div class="p-row">
      <span class="p-price"><span class="cur">Rs</span><span class="amt">27,300</span></span>
      <a class="p-wa" href="WHATSAPP_LINK" data-nomodal>...</a>
    </div>
  </div>
</article>
```

- To change the **price**, edit the number inside `<span class="amt">`.
- To change the **image**, replace the `src` link with a new image URL (images are currently hosted on iftikharelectronics.pk, not stored inside the file).
- To change the **name or brand**, edit the text inside `<h3 class="p-name">` or `<span class="p-brand">`.
- To mark something **out of stock**, change `In stock` to `Out of stock` inside `<span class="p-stock">`.

**Important:** There is a second copy of every product's information near the bottom of the file inside a block that starts with `window.__CATALOG__ = [...]`. This is what powers the product detail popup. If you add or remove a product, this list must also be updated, or the popup for that product will not work correctly. If you're not comfortable editing this part yourself, it's safest to ask for help rather than risk breaking the popup for other products.

---

## How to Add a Brand-New Product

Adding a new product safely means copying an existing product block in the same category, changing its details, and also adding a matching entry to the `window.__CATALOG__` list mentioned above. Because a mistake here can affect the whole category's layout (some categories use a grid pattern where the number of products affects how evenly they line up), it's recommended to get help when adding new products rather than doing it directly on the live file.

---

## Hosting / Deployment

This is a static file — it does not need a database or server-side code. It can be hosted on:

- Any standard shared hosting (upload `index.html` as the homepage)
- GitHub Pages, Netlify, Vercel, or similar free static hosting
- The current domain: iftikharelectronics.pk

No build step, no installation, and no dependencies are required — the file works as soon as it's uploaded.

---

## File Structure

```
index.html    → the entire website (HTML + CSS + JavaScript + logo, all in one file)
README.md     → this file
```

---

## Notes for Future Edits

- Do not change the color variables at the top of the file (`--navy-900`, `--amber-500`, etc.) without also checking the logo, since the logo's outline color was matched exactly to `--amber-500`.
- The WhatsApp number used throughout the site is `923460642661` (i.e. +92 346 0642661). If this number ever changes, it appears in many places throughout the file and every instance would need to be updated.
- Product images are linked from URLs on the iftikharelectronics.pk server, not stored inside `index.html`. If those images are ever moved or deleted from the server, they will stop showing on the site even though the file itself is unchanged.

---

## Credits

Developed by **Mahnoor Asim**.
