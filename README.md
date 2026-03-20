# kurtsaz.dev — Portfolio of Syed Mukhashif Hussain

> Plugin Developer specializing in OpenCart, WordPress & WooCommerce

[![GitHub Pages](https://img.shields.io/badge/Live%20Site-GitHub%20Pages-E8281A?style=flat-square&logo=github)](https://syedmukhashif.github.io/kurtsaz-portfolio)
[![License](https://img.shields.io/badge/License-MIT-0D0D0D?style=flat-square)](LICENSE)
[![OpenCart](https://img.shields.io/badge/OpenCart-3.x-34A2E0?style=flat-square)](https://opencart.com)
[![WordPress](https://img.shields.io/badge/WordPress-Plugin%20Dev-21759B?style=flat-square&logo=wordpress)](https://wordpress.org)
[![WooCommerce](https://img.shields.io/badge/WooCommerce-Engineering-96588A?style=flat-square)](https://woocommerce.com)

---

## About This Portfolio

This is my personal developer portfolio showcasing two real-world plugin development projects — a large-scale e-commerce migration and a custom bidding extension — both built from scratch with deep stress testing and zero tolerance for bugs.

**Live at:** [ https://syedmukhashif.github.io/OW-Product-Exporter/ ]

---

## Projects Featured

### Project Hermes — OpenCart to WooCommerce Migration

A real-world migration of **4,068 products** and **221 Greek-language categories** from OpenCart 3.x to WooCommerce for AMB Tobaccos & More.

**The challenge:** The official WooCommerce CSV importer kept failing. Products were importing as "Private". Only 3 of 221 categories were transferring. The root cause — the store ran on Greek (`language_id = 2`), but every query was hardcoded to English (`language_id = 1`).

**The solution:** Built a two-plugin system from scratch:

| Plugin | Purpose |
|--------|---------|
| `woo_transfer_api_v6.ocmod.zip` | REST API on OpenCart — exposes all store data |
| `oc-transfer-v6-clean.zip` | WordPress importer — pulls and imports with real-time UI |

**The result:**

```
[20:45:11] Complete! 4018 imported, 50 updated, 0 failed
Total time: 56 minutes | Products: 4,068 | Failures: 0
```

**26 bugs found and fixed during stress testing** before a single byte went to production.

---

### Project Agora — Proposal Bidding Extension

A custom OpenCart extension enabling buyers and sellers to negotiate prices directly within the store. Named after the ancient Greek marketplace.

**Features:**
- Proposal submission with price, quantity, and notes
- Counter-offer conversation threading
- Email notifications at every status change
- Admin dashboard with conversion tracking
- One-click acceptance that auto-creates an order
- Role-based access control

---

## Downloadable Plugins

Both plugins from Project Hermes are **free and open to use.**

### OpenCart API Plugin — `woo_transfer_api_v6.ocmod.zip`

Install on your **OpenCart store** to expose a secure transfer API.

**Features:**
- Auto-detects store language (Greek, English, or any)
- Batch database queries — no N+1 performance issues
- Proper HTTPS image URL encoding for all edge cases
- Duplicate SKU prevention within each batch
- Sale prices with date range validation
- Timing-safe API key authentication
- PHP 5.6+ and OpenCart 3.x compatible

**Installation:**
1. Go to OpenCart Admin → Extensions → Extension Installer
2. Upload `woo_transfer_api_v6.ocmod.zip`
3. Go to Extensions → Modifications → click Refresh
4. Visit `https://your-store.com/index.php?route=api/transfer/index&key=YOUR_KEY`

---

### WordPress Importer Plugin — `oc-transfer-v6-clean.zip`

Install on your **WordPress/WooCommerce site** to pull and import from OpenCart.

**Features:**
- Real-time progress bar and live log console
- Resume capability — if transfer crashes, saves page to localStorage
- Auto-retry up to 3 times with exponential backoff
- Category hierarchy preserved correctly using OC ID meta mapping
- Brand support via Perfect Brands for WooCommerce plugin
- SEO meta written for Yoast, RankMath, and SEOPress
- Zero duplicates on re-run — detects existing products by SKU and OC ID

**Installation:**
1. Go to WordPress Admin → Plugins → Add New → Upload Plugin
2. Upload `oc-transfer-v6-clean.zip` and activate
3. Go to OC Transfer in your WordPress sidebar
4. Enter your OpenCart URL and API key
5. Click Test Connection → Import Categories → Import Products

---

## Compatibility

| Requirement | Version |
|------------|---------|
| PHP | 7.2+ (tested on 7.2.34) |
| OpenCart | 3.0.x |
| WordPress | 5.0+ |
| WooCommerce | 5.0+ |
| MySQL | 5.7+ |

---

## Repository Structure

```
kurtsaz-portfolio/
├── index.html              # Portfolio site (single-file, self-contained)
├── plugins/
│   ├── woo_transfer_api_v6.ocmod.zip    # OpenCart API plugin
│   └── oc-transfer-v6-clean.zip         # WordPress importer plugin
├── README.md               # This file
├── LICENSE                 # MIT License
├── .gitignore              # Git ignore rules
└── .github/
    └── ISSUE_TEMPLATE/
        ├── bug_report.md   # Bug report template
        └── feature_request.md
```

---

## Tech Stack Used

```
Backend (OpenCart Plugin)
├── PHP 5.6+
├── OpenCart MVC architecture
├── MySQL batch queries
└── REST API (JSON)

Backend (WordPress Plugin)
├── PHP 7.2+
├── WordPress Hooks & AJAX
├── WooCommerce product meta API
└── wp_remote_get HTTP client

Frontend (Portfolio Site)
├── Vanilla HTML/CSS/JS (zero dependencies)
├── Google Fonts (Playfair Display + DM Sans + DM Mono)
├── CSS custom properties
├── IntersectionObserver API
└── CSS animations & keyframes
```

---

## Contact

| Platform | Link |
|---------|------|
| GitHub | [@SyedMukhashif](https://github.com/SyedMukhashif) |
| Instagram | [@kurtsaz](https://instagram.com/kurtsaz) |
| LinkedIn | [Syed Mukhashif Hussain](https://linkedin.com/in/syed-mukhashif) |
| Email | [we.kurtsaz@gmail.com](mailto:we.kurtsaz@gmail.com) |

---

## License

This portfolio and the plugins within it are released under the [MIT License](LICENSE).

You are free to use, copy, modify, and distribute the plugins for any purpose, commercial or personal, with or without attribution.

---

*Built with deep thinking, stress testing, and zero tolerance for bugs.*

---

## Quick Deploy Commands

```bash
# Clone or init your repo
git init
git add .
git commit -m "feat: initial portfolio launch — Project Hermes & Agora"
git branch -M main
git remote add origin https://github.com/SyedMukhashif/kurtsaz-portfolio.git
git push -u origin main
```

Then go to **Settings → Pages → Source: main branch / root** and your site will be live at:
[ https://syedmukhashif.github.io/OW-Product-Exporter/ ]
