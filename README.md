# ✈️ Travel Flow — Journey Beyond the Horizon

> 🌊 Albania's most extra travel platform. Yes, really.

**Book** a bus seat · **Track** it live on a map · **Rent** a car · **Explore** the Riviera

---

## 🤔 Wait, what is this?

You ever tried to book a bus in Albania? It's usually... an adventure. 

Travel Flow fixes that. It's a full travel platform for the Albanian Riviera — book a seat, track your bus live on a map, rent a car and drive those insane coastal roads yourself, or just browse destinations until you're ready to quit your job and move there.

The wild part? **It's one single HTML file.** No backend. No npm. No Docker. No cloud bill. Just open it and it works. 🧙

> Built with love, vanilla JS, and an unhealthy obsession with Albanian road coordinates.

---

## 🔥 Features

### 🎫 Ticket Booking
- Search by route, date and time
- Visual bus seat map — green = free, red = taken
- Pick your exact seat like a civilized human
- Card payment flow (simulated, but feels real)
- Instant ticket with unique code `TWS-XXXXXX`

### 📍 Live GPS Tracking
- Every bus on the map, moving in real time
- Updates every 2 seconds — no refreshing needed
- Sidebar shows `MOVING` / `STOPPED` status per bus
- Click any bus to zoom in and see its popup
- Progress bar showing % of route completed

### 🚗 Car Rental
- 5 cars: Economy, Compact, SUV, Luxury, Off-Road
- All cars GPS-tracked on the admin map
- Rented cars actually start driving around Albania
- Car auto-drives itself back to base when rental ends 🤯
- Price calculator updates live as you pick dates

### 🗺️ Tourist Guide
| Destination | Highlights |
|---|---|
| 🌊 Sarandë | Crystal water, Butrint UNESCO, Ksamil beach |
| ⛵ Himarë | Porto Palermo castle, Gjipe beach, seafood |
| 🏙️ Tiranë | Bunk'Art, Blloku, Pazari i Ri, chaos & coffee |
| 🏖️ Riviera | 130km of untouched Ionian coastline |
| 🦅 Llogara | National park, eagles, 1043m panoramic views |
| 🏛️ Butrint | Greek + Roman + Byzantine + Venetian. All in one. |

### 👤 User Accounts
- Register / Login with session persistence
- View all your bookings with ticket codes
- View all your rentals and their status
- Admins get a secret extra link in the navbar 🕵️

### ⚙️ Admin Panel *(login as admin to unlock)*
- Dashboard: bookings, users, buses, total revenue
- Fleet management: all 6 buses with live coordinates
- Cars GPS: live map with **all** vehicles moving simultaneously
- Full bookings, users and rentals management

---

## 🛣️ The Routes

| Route | Distance | Duration | Price |
|---|---|---|---|
| Tiranë → Himarë | 234 km | 4h 30min | 1,200 ALL |
| Tiranë → Sarandë | 284 km | 5h 30min | 1,500 ALL |
| Himarë → Sarandë | 62 km | 1h 30min | 500 ALL |
| Sarandë → Himarë | 62 km | 1h 30min | 500 ALL |
| Sarandë → Tiranë | 284 km | 5h 30min | 1,500 ALL |
| Himarë → Tiranë | 234 km | 4h 30min | 1,200 ALL |

The full Tiranë → Sarandë route hits:
`SH2 → A1 Autostrada → Bypass Kavajë → A2 → Vlorë → SH8 Rivierë → Orikum → Qafa e Llogarasë → Palasë → Dhërmi → Himarë → Porto Palermo → Borsh → Sarandë`

> 🦅 **Qafa e Llogarasë** deserves a special mention: 1,043 meters above the Ionian Sea, 48 hairpin turns, pine forests, eagle nests. Every single curve is coded as a GPS waypoint. Yes, all 48. We counted. We regret nothing.

---

## 🚀 Quick Start

```bash
git clone https://github.com/your-username/travelflow.git
cd travelflow
open index.html
```

That's it. No `npm install`. No `pip install`. No `docker-compose up`. Just a file in a browser.

### 🔑 Demo Accounts

| Role | Email | Password |
|---|---|---|
| 🔴 Admin | admin@travelflow.al | admin123 |
| 🔵 User | arben@test.al | test123 |

> **Tip:** Login as admin first — the Cars GPS section alone is worth it.

---

## 🛰️ How the GPS Engine Actually Works

Most "live tracking" demos just ping between two points in a straight line and call it a day. That felt wrong.

Travel Flow uses **cumulative distance interpolation**:

1. Every route has hundreds of real GPS waypoints verified manually on OpenStreetMap satellite view
2. On each 2-second tick, the engine calculates how far along the total route the vehicle should be
3. It finds the exact segment and interpolates the precise lat/lng within it

**Result:** vehicles follow actual road curves, hug the coastline, and navigate every mountain switchback correctly.

- 🚌 **6 buses** — each on its own route, bouncing end to end with pause time at terminals
- 🚗 **5 cars** — roam 9 different routes across Albania; when rented they start driving, when the rental expires they drive themselves home 🏠

> Base: **New Regional Bus Terminal, Kashar, Tiranë** — `41.33319°N, 19.80291°E`

---

## 🛠️ Tech Stack

| Technology | What it does |
|---|---|
| Vanilla JS (ES6+) | All app logic, GPS engine, routing |
| CSS3 Custom Properties | Dark theme, animations, responsive layout |
| Leaflet.js 1.9.4 | Interactive maps |
| OpenStreetMap | Map tiles — no Google Maps bill 🙏 |
| Font Awesome 6.5 | Icons |
| Google Fonts | Cormorant Garamond · DM Sans · Bebas Neue |
| `localStorage` | Our "database" 😇 |

---

## 🏗️ Code Structure

Everything lives inside `index.html`:

```
index.html
├── <style>         Dark navy theme, CSS vars, all component styles
├── <body>          7 pages toggled by JS class switching
│   ├── #page-home      Hero + routes + features + footer
│   ├── #page-book      Search + trip cards + seat map + payment
│   ├── #page-track     Live GPS sidebar + Leaflet map
│   ├── #page-guide     Destination cards
│   ├── #page-rental    Car grid + rental modal
│   ├── #page-account   My bookings + my rentals
│   └── #page-admin     Dashboard + 7 admin sections
└── <script>
    ├── ROUTE_DATA      6 routes with metadata
    ├── WAYPOINTS       Hundreds of real GPS coordinates
    ├── CAR_ROUTES      9 car routes across Albania
    ├── DB              localStorage wrapper (get / set / seed)
    ├── GPS             Position engine + Leaflet marker control
    ├── Auth            Login / Register / Session
    └── UI functions    Page render, modals, toasts, search
```

---

## 👥 Stakeholders

**Internal**
- Travel Flow Company — wants profit and a working product
- System Administrator — wants full control and live data
- Bus Operator — wants accurate schedules

**External**
- Local Traveler — wants cheap, easy booking
- International Tourist — wants GPS, car rental, beach guide
- Car Renter — wants transparent pricing
- ARRSH Authority — wants legal compliance
- Insurance Company — wants fleet data
- OpenStreetMap / GPS — provides infrastructure
- Local Municipality — wants more tourists

**Negative Stakeholders** *(yes, they count too 😤)*
- FlixBus / Eurolines — competing on price and routes
- Booking.com / Google Travel — stealing users with bundled deals
- Informal Minibuses — no rules, lower prices, zero GPS

---

## 🔮 Roadmap

- [ ] Real database — Firebase Firestore or PostgreSQL
- [ ] Backend API — Node.js / Express or Python / Flask
- [ ] Real payments — Stripe integration
- [ ] Email tickets — PDF on booking confirmation
- [ ] SMS alerts — *"Your bus departs in 30 minutes"*
- [ ] Multi-language — Albanian · English · Italian
- [ ] Mobile app — PWA or React Native
- [ ] More routes — Gjirokastër, Korçë, Shkodër
- [ ] Bus operator app — separate dashboard for drivers
- [ ] Reviews & ratings — let passengers rate the ride

---

---

## ✍️ Author

**Travel Flow Team** · Tiranë, Shqipëri 🇦🇱  
📧 info@travelflow.al

Made with ❤️ and an unreasonable amount of ☕  
*Powered by the dream that Albanian bus travel can be good, actually.*

If this helped you or made you smile, leave a ⭐ on GitHub.  
If you found a bug, open an issue — or just blame the hairpin turns.

---

<div align="center">
  <b>Tiranë · Himarë · Sarandë · Llogara · Butrint</b><br>
  <i>The Albanian Riviera is waiting. ✈️ 🌊</i>
</div>

---

*© 2025 Travel Flow Agency. All rights reserved.*
