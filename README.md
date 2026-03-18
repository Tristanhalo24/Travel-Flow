# ✈️ Travel Flow — Journey Beyond the Horizon

> 🌊 Albania's most extra travel platform. Yes really.

**Book** a bus seat · **Track** it live on a map · **Rent** a car · **Explore** the Riviera

---

## 🤔 Wait, what is this?

You ever tried to book a bus in Albania? It's usually... an adventure. 

Travel Flow fixes that. It's a full travel platform for the Albanian Riviera — book a seat, track your bus live on a map, rent a car and drive those insane coastal roads yourself, or just browse destinations until you're ready to quit your job and move there.

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
- 12 cars: Economy, Compact, SUV, Luxury, Off-Road
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

## 🛰️ How the GPS Engine Actually Works

Most "live tracking" demos just ping between two points in a straight line and call it a day. That felt wrong.

Travel Flow uses **cumulative distance interpolation**:

1. Every route has hundreds of real GPS waypoints verified manually on OpenStreetMap satellite view
2. On each 2-second tick, the engine calculates how far along the total route the vehicle should be
3. It finds the exact segment and interpolates the precise lat/lng within it

**Result:** vehicles follow actual road curves, hug the coastline, and navigate every mountain switchback correctly.

- 🚌 **6 buses** — each on its own route, bouncing end to end with pause time at terminals
- 🚗 **12 cars** — roam 9 different routes across Albania; when rented they start driving, when the rental expires they drive themselves home 🏠

> Base: **New Regional Bus Terminal, Kashar, Tiranë** — `41.33319°N, 19.80291°E`

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

- [ ] Real database — MYSQL
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

<div align="center">
  <b>Tiranë · Himarë · Sarandë · Llogara · Butrint</b><br>
  <i>The Albanian Riviera is waiting. ✈️ 🌊</i>
</div>

---

*© 2025 Travel Flow Agency. All rights reserved.*
