# ✈️ Travel Flow — Journey Beyond the Horizon

> 🌊 Albania's most extra travel platform. Yes really.

**Book** a bus seat · **Track** it live on a map · **Rent** a car · **Validate** tickets · **Explore** the Riviera

---

## 🤔 Wait, what is this?

You ever tried to book a bus in Albania? It's usually... an adventure.

Travel Flow fixes that. It's a full travel platform for the Albanian Riviera — book a seat, track your bus live on Google Maps, rent a car and drive those insane coastal roads yourself, or just browse destinations until you're ready to quit your job and move there.

---

## 🔥 Features

### 🎫 Ticket Booking
- Search by route, date and time
- Visual bus seat map — green = free, grey = taken, gold = your random pick
- Pick your exact seat (+200 ALL) or get a random one for free
- Real card validation: Visa, Mastercard, Amex with **Luhn algorithm** check
- Live card type detection with brand logo as you type
- Expiry date and CVV validation before processing
- Instant e-ticket with unique code `TRF-XXXXXX`
- **Email delivery** — ticket sent to your inbox after booking (barcode included)

### 📧 Email Verification
- New accounts require email verification before creation
- 6-digit code sent via EmailJS on registration
- Resend code option if it doesn't arrive
- Verified accounts only — no throwaway signups

### 📍 Live GPS Tracking (Google Maps)
- Real road paths fetched from **Google Directions API** on load
- Every bus follows the actual road — every curve, every switchback on Qafa e Llogarasë
- Updates every 2 seconds — no refreshing needed
- Sidebar shows `MOVING` / `STOPPED` status with progress bar per bus
- Click any bus marker to see route and plate in popup
- All 6 buses running simultaneously on different routes

### 🚗 Car Rental
- 12 cars: Economy, Compact, SUV, Luxury, Off-Road
- Real car photos for every vehicle
- All cars GPS-tracked on the admin map using Google Maps
- Rented cars start driving real Albanian road routes immediately
- Car auto-drives itself back to base when rental expires 🤯
- Live price calculator updates as you pick dates
- Payment flows through same card validation as ticket booking

### 🚌 Driver Panel *(driver login required)*
- Dedicated panel showing the driver's assigned bus and route
- Manual ticket validation by typing a booking code
- **QR code camera scanner** — scan printed tickets with device camera
- Real-time validation result: ✅ Valid / ❌ Not Found / ⚠️ Already Scanned
- Running log of all tickets validated that session with timestamps
- Counter showing total validations for the day

### 🗺️ Tourist Guide
| Destination | Highlights |
|---|---|
| 🌊 Sarandë | Crystal water, Butrint UNESCO, Ksamil beach |
| ⛵ Himarë | Porto Palermo castle, Gjipe beach, seafood |
| 🏖️ Albanian Riviera | 130km of untouched Ionian coastline |
| 🦅 Llogara Pass | National park, eagles, 1043m panoramic views |
| 🏛️ Butrint | Greek + Roman + Byzantine + Venetian. All in one. |
| 🏰 Porto Palermo | Ottoman castle on a perfect turquoise bay |

### 👤 User Accounts
- Register with email verification, login with session persistence
- View all bookings with ticket codes and seat details
- View all rentals with status (confirmed / returning / completed)
- User dropdown menu in navbar with quick-access links
- Admins get a gold ⚙️ Admin link · Drivers get a green 🚌 Driver link

### 🔧 Fleet Maintenance
- Public maintenance view for all 6 buses and 12 cars
- Filter by: All / Buses Only / Cars Only / Due & Overdue
- Per-vehicle health score shown as a progress bar
- Service status: ✅ All Good · ⚠️ Due Soon · 🔴 Overdue
- Admin version includes **interactive checkboxes** to mark services as done
- Checking a service auto-updates its next service date based on interval
- "Mark All as Serviced" button per vehicle for bulk updates

### ⚙️ Admin Panel *(admin login required)*
- **Dashboard** — bookings, users, buses, total revenue at a glance
- **Buses** — full fleet table with live GPS status (Moving / Stopped)
- **Routes** — all 6 routes with distance, duration, full price, min price, stop count
- **Bookings** — complete table with fee breakdown (ticket + site fee + seat fee)
- **Users** — full user list with roles and registration dates
- **Cars GPS** — photo grid of all cars + live Google Map with all vehicles moving
- **Rentals** — rental history with status tracking (confirmed / returning / completed)
- **Maintenance** — interactive checkbox-based service management
- **Finances** — full financial analysis across 6 tabs (see below)

### 💰 Finance Panel *(admin only)*
Six dedicated tabs covering the full picture:

| Tab | What's Inside |
|---|---|
| 📊 Overview | Daily/monthly/yearly revenue, profit margin, revenue bar chart by route |
| 💵 Revenue | Monthly bar chart, seasonal comparison, year-over-year growth table |
| 👷 Salaries | Driver pay (10% of round-trip revenue), ticket collector pay (4,000 ALL/leg), office staff fixed salaries |
| 📅 Schedule | Full driver and ticket collector timetable with departure/arrival times |
| 📋 Expenses | Fuel per bus, maintenance, insurance, inspection, taxes, rent, utilities |
| 📈 Profit | Daily P&L breakdown, monthly seasonal profit chart, full 12-month table |

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

> 🦅 **Qafa e Llogarasë** deserves a special mention: 1,043 meters above the Ionian Sea, 48 hairpin turns, pine forests, eagle nests. The GPS engine traces every curve via Google Directions API. We regret nothing.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML/CSS/JS — no framework, no build step |
| Maps | Google Maps JavaScript API + Directions API |
| Email | EmailJS (verification codes + ticket delivery) |
| QR Scanning | html5-qrcode library |
| Fonts | Cormorant Garamond · DM Sans · Bebas Neue (Google Fonts) |
| Icons | Font Awesome 6.5 |
| Storage | localStorage (client-side DB, seeds on first load) |

---

## 🛰️ How the GPS Engine Actually Works

Most "live tracking" demos just ping between two points in a straight line. That felt wrong.

Travel Flow uses **real road paths + cumulative distance interpolation**:

1. On page load, **Google Directions API** fetches the actual road geometry for all bus routes, including the TR-HI via Vlorë, Orikum and Llogara Pass
2. Car routes (12 routes across Albania) are also fetched from Directions API in parallel
3. On each 2-second tick, the engine calculates how far along the total route each vehicle should be
4. It finds the exact segment and interpolates the precise lat/lng within it
5. Fallback waypoints are used if the API call fails

**Result:** vehicles follow real tarmac, hug the coastline, and navigate every mountain switchback correctly.

- 🚌 **6 buses** — each on its own route, bouncing end-to-end with pause time at terminals
- 🚗 **12 cars** — roam 12 different road routes across Albania; when rented they start driving, when the rental expires they drive themselves home 🏠

> Base: **New Regional Bus Terminal, Kashar, Tiranë** — `41.343°N, 19.777°E`

---

## 🔐 Demo Accounts

| Role | Email | Password |
|---|---|---|
| Admin | admin@travelflow.al | admin123 |
| Driver (BUS001, TR-HI) | agron@travelflow.al | driver123 |
| Driver (BUS002, TR-SA) | bashkim@travelflow.al | driver123 |
| Client | arben@test.al | test123 |

---

## 👥 Stakeholders

**Internal**
- Travel Flow Company — wants profit and a working product
- System Administrator — wants full control and live data
- Bus Drivers — want a scanning tool and their schedule
- Ticket Collectors (Faturinot) — want shift info and daily pay tracking

**External**
- Local Traveler — wants cheap, easy booking
- International Tourist — wants GPS, car rental, beach guide
- Car Renter — wants transparent pricing and GPS tracking
- ARRSH Authority — wants legal compliance
- Insurance Company — wants fleet maintenance data
- OpenStreetMap / Google Maps — provides geographic infrastructure
- Local Municipality — wants more tourists

**Negative Stakeholders** *(yes, they count too 😤)*
- FlixBus / Eurolines — competing on price and routes
- Booking.com / Google Travel — stealing users with bundled deals
- Informal Minibuses — no rules, lower prices, zero GPS

---

## 🔮 Roadmap

- [ ] Real database — MySQL / SQL Server (schema already written)
- [ ] Backend API — Node.js / Express or ASP.NET Core
- [ ] Real payments — Stripe integration
- [ ] PDF tickets — generated and attached to confirmation email
- [ ] SMS alerts — *"Your bus departs in 30 minutes"*
- [ ] Multi-language — Albanian · English · Italian
- [ ] Mobile app — PWA or React Native
- [ ] More routes — Gjirokastër, Korçë, Shkodër, Berat
- [ ] Driver app — standalone mobile dashboard
- [ ] Reviews & ratings — let passengers rate the ride

---

## 🗄️ Database

A full SQL Server (T-SQL) schema is included in the repo covering:

`Users · Routes · Stops · Buses · Trips · BookedSeats · Bookings · Cars · Rentals · Maintenance · MaintenanceServices · Drivers · TicketCollectors · OfficeStaff · ValidatedTickets`

Plus views (`vw_TripAvailability`, `vw_RouteRevenue`, `vw_ActiveRentals`, `vw_MaintenanceOverdue`) and stored procedures (`sp_SearchTrips`, `sp_ConfirmBooking`, `sp_RentCar`, `sp_ValidateTicket`, `sp_MarkServiceDone`).

---

<div align="center">
  <b>Tiranë · Himarë · Sarandë · Llogara · Butrint</b><br>
  <i>The Albanian Riviera is waiting. ✈️ 🌊</i>
</div>

---

*© 2025 Travel Flow Agency. All rights reserved.*
