# Ahmed Ultrasound Website
## 30-Day Product + Learning Execution Plan

**Project Duration:** 30 Days  
**Primary Goal:** Learn Frontend through building a real production website  
**Delivery Goal:** Production website live by Day 30

---

# 1. Final Product

الموقع عبارة عن جزئين:

## Public Website

الزائر يقدر:

- يشوف Landing Page.
- يتصفح أجهزة السونار.
- يعمل Search.
- يعمل Filter حسب Brand وStatus.
- يدخل صفحة تفاصيل أي جهاز.
- يشوف صور الجهاز.
- يشوف أهم بياناته.
- يعرف هل الجهاز:
  - Available
  - Reserved
  - Sold
- يتواصل على WhatsApp بخصوص الجهاز.

## Admin CMS

أحمد يقدر:

- يعمل Login.
- يشوف كل الأجهزة.
- يضيف جهاز.
- يعدل جهاز.
- يحذف جهاز.
- يغير حالته.
- يرفع صور.
- يحذف/يستبدل صور.

---

# 2. Final Tech Stack

## Frontend Learning Phase

- HTML5
- CSS3
- Vanilla JavaScript

## Final Frontend

- React
- Vite
- React Router
- Plain CSS
- Native Fetch API

## Backend

- Python
- FastAPI

## Database

- PostgreSQL
- Hosted PostgreSQL مثل Neon

## Database Integration

- SQLModel

## Authentication

- FastAPI
- Password hashing
- JWT Bearer Authentication

FastAPI documentation currently uses JWT-based authentication with secure password hashing as a standard implementation approach.

## Image Storage

- Cloudinary

Cloudinary supports server-side image uploads through its Python SDK and returns URLs/metadata that we can save in PostgreSQL.

## Deployment

- Vercel
- Frontend + FastAPI can live in the same repository.

Vercel currently supports FastAPI through its Python runtime, including deploying FastAPI applications as Vercel Functions.

---

# 3. Simplified Data Model

## Device

```text
id
brand
model
description
condition
year
status
price
created_at
updated_at
```

### status

```text
available
reserved
sold
```

### price

Optional.

---

## DeviceImage

```text
id
device_id
image_url
public_id
position
created_at
```

`public_id` هنحتاجه علشان نقدر نحذف الصورة من Cloudinary.

---

## Admin

```text
id
email
password_hash
created_at
```

Admin واحد فقط في الـMVP.

لا يوجد Registration.

---

# 4. API Contract

## Public

```text
GET /api/devices
GET /api/devices/{id}
```

## Admin

```text
POST   /api/devices
PATCH  /api/devices/{id}
DELETE /api/devices/{id}
```

## Auth

```text
POST /api/auth/login
GET  /api/auth/me
```

## Images

```text
POST   /api/devices/{id}/images
DELETE /api/devices/{id}/images/{image_id}
```

---

# 5. 30-Day Execution Plan

---

# PHASE 1 — HTML + CSS
## Days 1–6

---

## Day 1 — Project Setup

### Learning

- Git basics
- GitHub
- npm basics
- Browser DevTools
- Project structure
- Development workflow

### Tasks

- Create GitHub repository.
- Create project folders.
- Add `.gitignore`.
- Create initial `index.html`.
- Create `styles.css`.
- Link CSS.
- Build basic HTML shell.
- Make first commits.

Initial structure:

```text
ahmed-ultrasound/
├── frontend/
│   ├── index.html
│   ├── css/
│   │   └── styles.css
│   └── assets/
│
├── backend/
│
└── README.md
```

### Deliverable

Static page running locally.

### Definition of Done

You can:

- edit
- inspect
- test
- commit
- push

without help.

---

## Day 2 — HTML Structure

### Learning

- Semantic HTML
- Sections
- Headings
- Images
- Links
- Buttons

### Build

Landing page HTML:

```text
Navbar
Hero
Devices Preview
Services
Why Us
Contact CTA
Footer
```

No serious styling yet.

### Deliverable

Full landing-page structure.

### Definition of Done

The entire page content exists in semantic HTML.

---

## Day 3 — CSS Foundations

### Learning

- Selectors
- Cascade
- Specificity
- Inheritance
- Box model
- Margin
- Padding
- Typography
- Colors
- Borders
- Shadows
- CSS variables

### Build

Style:

- Navbar
- Hero
- Buttons
- Section headings
- Cards
- Footer

### Deliverable

Desktop landing page visually recognizable.

---

## Day 4 — Flexbox + Containers

### Learning

- Flexbox
- `gap`
- Alignment
- Container pattern
- `max-width`

### Build

Fix:

- Navbar alignment
- Hero layout
- CTA sections
- Service cards
- Footer layout

### Deliverable

Clean desktop layout.

---

## Day 5 — CSS Grid + Catalogue Layout

### Learning

- CSS Grid
- responsive card layouts
- reusable CSS classes

### Build

Create device card grid.

Hard-code 6 example ultrasound devices.

Each card:

```text
image
brand
model
status
price/contact
details button
```

### Deliverable

Desktop catalogue section.

---

## Day 6 — Responsive Design

### Learning

- Media queries
- Relative units
- responsive images
- overflow
- positioning
- mobile-first thinking

### Test Widths

```text
320px
768px
1024px
Desktop
```

### Build

- Mobile navbar.
- Responsive Hero.
- Responsive grid.
- Responsive footer.
- Fix image sizing.

### Deliverable

Fully responsive static website.

### Phase Gate

Do not continue unless the landing page genuinely works on mobile and desktop.

---

# PHASE 2 — VANILLA JAVASCRIPT
## Days 7–12

---

## Day 7 — JavaScript Device Data

### Learning

- `const`
- arrays
- objects
- functions
- modules

### Build

Create:

```js
devices.js
```

With realistic device objects.

Example:

```js
{
  id: 1,
  brand: "GE",
  model: "Voluson E10",
  status: "available",
  condition: "used",
  year: 2022
}
```

### Exercises

Write functions:

```text
getAvailableDevices()
getSoldDevices()
getDevicesByBrand()
getDeviceById()
```

### Deliverable

Device dataset + utility functions.

---

## Day 8 — Array Methods

### Learning

Deep practice with:

```text
map
filter
find
some
destructuring
spread
template literals
```

### Build

Implement:

- filter by brand.
- filter by status.
- search by model.
- device counters.

### Deliverable

All catalogue data operations work in JavaScript.

---

## Day 9 — DOM Rendering

### Learning

- DOM
- `querySelector`
- events
- rendering
- `dataset`
- classes

### Build

Remove hard-coded device cards.

Generate them from JavaScript data.

```text
devices array
     ↓
renderDevices()
     ↓
HTML cards
```

### Deliverable

Catalogue generated entirely from JS.

---

## Day 10 — Interactive Catalogue

### Build

Add:

- Brand filter.
- Status filter.
- Search.
- Clear filters.
- No-results message.
- Mobile menu interaction.

### Learning

Understand:

```text
Data
 ↓
State
 ↓
Render
 ↓
User Event
 ↓
State changes
 ↓
Render again
```

### Deliverable

Fully interactive Vanilla JS catalogue.

---

## Day 11 — HTTP + Async JavaScript

### Learning

- Promise
- `async/await`
- Fetch API
- JSON
- GET
- POST
- PATCH
- DELETE
- HTTP status codes
- try/catch

### Backend Task

Create minimal FastAPI project:

```text
backend/
├── main.py
├── models.py
└── requirements.txt
```

Initially keep devices in memory.

Implement:

```text
GET /api/devices
GET /api/devices/{id}
```

### Deliverable

Opening `/docs` shows working FastAPI API.

---

## Day 12 — Vanilla JS → FastAPI

Remove local device dataset from the UI.

Fetch devices:

```text
Vanilla JS
   ↓
fetch()
   ↓
FastAPI
```

Add:

- loading state.
- error state.
- retry.
- empty state.

### Deliverable

Catalogue loads from real HTTP API.

### Phase Gate

You should understand exactly what happens between:

```js
fetch(...)
```

and:

```python
@app.get(...)
```

---

# PHASE 3 — REACT
## Days 13–19

---

## Day 13 — React + Vite Setup

### Learning

- Vite
- JSX
- React app structure
- Components

Create React frontend.

### Build

Recreate:

```text
Navbar
Hero
Services
Footer
```

in React.

No API yet.

### Deliverable

React landing-page shell.

---

## Day 14 — Component Architecture

### Create

```text
App
├── Navbar
├── Hero
├── DevicesSection
│   ├── DeviceFilters
│   └── DeviceCard
├── ContactCTA
└── Footer
```

### Learning

- props
- composition
- lists
- keys
- conditional rendering

### Deliverable

Device cards generated from an array through React.

---

## Day 15 — React + FastAPI

Connect React to:

```text
GET /api/devices
```

### Implement

- `useState`
- loading
- errors
- fetch
- data rendering

### Deliverable

React catalogue uses FastAPI data.

---

## Day 16 — React State & Filters

Move catalogue interaction into React.

### Implement

- search.
- status filter.
- brand filter.
- reset.
- derived results.
- no-results state.

### Learning

- ownership of state.
- lifting state.
- derived state.
- immutable thinking.

### Deliverable

Interactive React catalogue.

---

## Day 17 — Controlled Inputs

Refactor filters into proper controlled components.

### Learn

- controlled inputs
- form events
- reusable form elements

### Build

Reusable:

```text
SearchInput
Select
StatusBadge
Button
```

### Deliverable

Clean component/state structure.

---

## Day 18 — React Router

Install React Router.

Routes:

```text
/
/devices
/devices/:id
/contact
/admin
*
```

### Build

- layouts.
- navigation.
- 404 page.
- URL params.

### Deliverable

Multi-page SPA navigation.

---

## Day 19 — Device Details + WhatsApp

Build:

```text
/devices/:id
```

Display:

- images.
- brand.
- model.
- condition.
- year.
- status.
- description.
- optional price.

### WhatsApp CTA

Generate device-specific message:

```text
Hello, I want to ask about GE Voluson E10
```

### Deliverable

Complete customer journey:

```text
Home
↓
Catalogue
↓
Device
↓
WhatsApp
```

### Phase Gate

Public website core flow must now work.

---

# PHASE 4 — ADMIN CMS
## Days 20–26

---

## Day 20 — Admin UI

Build admin layout:

```text
/admin
/admin/devices
/admin/devices/new
/admin/devices/:id/edit
```

### UI

- Sidebar.
- Header.
- Devices table.
- Add Device button.
- Edit/Delete actions.
- Status badges.

Use mock data initially.

### Deliverable

Complete admin visual structure.

---

## Day 21 — Device Form

Build reusable:

```text
DeviceForm
```

Fields:

```text
Brand
Model
Description
Condition
Year
Status
Price
```

### Learn

- larger controlled form.
- validation.
- errors.
- submit states.

Use the same form for Add and Edit.

### Deliverable

Add/Edit forms work locally.

---

## Day 22 — PostgreSQL Persistence

Now replace FastAPI in-memory data.

### Backend

Connect FastAPI → PostgreSQL.

Implement database models.

FastAPI's official SQL guidance supports relational databases and illustrates ORM-style integration through SQLModel.

Create:

```text
admins
devices
device_images
```

### FastAPI CRUD

Implement:

```text
GET    /api/devices
GET    /api/devices/{id}
POST   /api/devices
PATCH  /api/devices/{id}
DELETE /api/devices/{id}
```

### Deliverable

CRUD persists after server restart.

---

## Day 23 — React Admin → Real CRUD

Connect Admin Dashboard to FastAPI.

### Implement

Create:

```text
Add Device
↓ POST
FastAPI
↓
PostgreSQL
```

Edit:

```text
Edit Device
↓ PATCH
FastAPI
↓
PostgreSQL
```

Delete:

```text
Delete
↓ Confirmation
↓ DELETE
FastAPI
```

### Deliverable

Full Device CRUD.

### Critical Acceptance Test

Add a device in Admin.

Then open public catalogue.

The device must appear.

---

## Day 24 — Authentication

### Backend

Create one Admin account.

Implement:

```text
POST /api/auth/login
GET /api/auth/me
```

Password stored as hash.

JWT returned after successful login.

### Frontend

Build:

```text
/admin/login
```

Implement:

- login.
- logout.
- token usage.
- protected routes.
- authorization errors.

### Deliverable

Visitor cannot access Admin Dashboard.

---

## Day 25 — Image Upload

Integrate Cloudinary.

### Learn

- File input.
- File object.
- `FormData`.
- previews.
- multipart requests.

### Flow

```text
React file input
       ↓
FastAPI
       ↓
Cloudinary
       ↓
URL + public_id
       ↓
PostgreSQL
```

### Implement

- Upload image.
- Show preview.
- Save image URL.
- Display image publicly.

### Deliverable

Admin uploads a real device image and visitor sees it.

---

## Day 26 — Complete CMS Integration

Finish:

- Multiple images.
- Delete image.
- Change device status.
- Sold/Reserved visual states.
- Delete device confirmation.
- API authorization checks.
- Public catalogue refresh.

### Full Integration Test

```text
Login
↓
Create device
↓
Upload image
↓
Available
↓
Public site displays device
↓
Change to Reserved
↓
Public site reflects Reserved
↓
Change to Sold
↓
Public site reflects Sold
↓
Delete
↓
Device disappears
```

### Deliverable

MVP functionality complete.

From here onward:

**No new major features.**

---

# PHASE 5 — PRODUCTION
## Days 27–30

---

## Day 27 — States & Accessibility

Audit:

```text
loading
error
empty
success
disabled
```

Test:

```text
0 devices
1 device
30 devices
long names
missing image
API error
slow network
```

### Accessibility

- Semantic HTML.
- Labels.
- Alt text.
- Keyboard navigation.
- Focus states.
- Button semantics.
- Heading hierarchy.

### Deliverable

Application handles real-world states.

---

## Day 28 — Responsive QA + SEO

Test every page:

```text
320px
768px
1024px
Desktop
```

Including Admin.

### SEO

Add:

- title.
- description.
- favicon.
- page metadata.
- Open Graph basics.
- useful device page titles.

### Performance

- image sizing.
- lazy loading where useful.
- remove unused assets.
- Lighthouse review.

### Deliverable

Production-polished UI.

---

## Day 29 — Production Deployment

Configure production infrastructure.

### Database

Create hosted PostgreSQL database.

### Images

Configure Cloudinary environment variables.

### Backend

Deploy FastAPI.

Vercel officially supports deploying FastAPI on its Python runtime.

### Frontend

Build production React app.

Configure:

```text
API URL
JWT secret
DATABASE_URL
Cloudinary credentials
```

Never expose backend secrets in frontend environment variables.

### Production Smoke Test

Test:

```text
GET devices
Login
Create
Edit
Upload
Delete
WhatsApp
```

### Deliverable

Website accessible through public URL.

---

# Day 30 — Final QA + Launch

No coding new features unless fixing a blocker.

Run full acceptance test.

## Public

### Home

- Loads correctly.
- Responsive.
- Navigation works.

### Catalogue

- Devices load.
- Search works.
- Brand filter works.
- Status filter works.

### Device Details

- Correct device.
- Images load.
- Data is correct.
- Status is correct.
- WhatsApp works.

### Contact

- Phone/WhatsApp links work.

---

## Admin

### Authentication

- Correct login works.
- Wrong password fails.
- Unauthorized visitor is blocked.
- Logout works.

### CRUD

- Create works.
- Read works.
- Edit works.
- Delete works.

### Status

```text
Available
Reserved
Sold
```

all work.

### Images

- Upload works.
- Display works.
- Delete works.

---

## Production Checks

- Refreshing routes works.
- No broken links.
- No console-breaking errors.
- Environment variables correct.
- Mobile works.
- HTTPS works.
- Database persists.
- Images persist.
- 404 works.
- API errors don't crash UI.

---

# 6. Day-30 Definition of Done

The project is officially complete when this exact scenario works:

```text
Ahmed opens website
↓
Clicks Login
↓
Logs into Admin
↓
Adds GE ultrasound device
↓
Uploads images
↓
Sets Available
↓
Saves
↓
Visitor opens public catalogue
↓
New device appears
↓
Visitor opens device details
↓
Clicks WhatsApp
↓
Message contains device name
↓
Ahmed changes device to Sold
↓
Public website shows Sold
```

If that works on both mobile and desktop:

**MVP = Done.**

---

# 7. Scope Locked for These 30 Days

## Included

```text
✅ Landing Page
✅ Responsive Design
✅ Catalogue
✅ Search
✅ Brand Filter
✅ Status Filter
✅ Device Details
✅ WhatsApp CTA
✅ Contact Page
✅ Admin Login
✅ Admin Dashboard
✅ Create Device
✅ Edit Device
✅ Delete Device
✅ Available / Reserved / Sold
✅ Multiple Images
✅ PostgreSQL
✅ FastAPI
✅ Production Deployment
```

## Explicitly Excluded

```text
❌ TypeScript
❌ Tailwind
❌ Next.js
❌ Redux
❌ Zustand
❌ shadcn
❌ React Hook Form
❌ Axios
❌ TanStack Query
❌ Shopping Cart
❌ Checkout
❌ Payments
❌ Customer Accounts
❌ Orders
❌ Inventory
❌ Reviews
❌ Wishlist
❌ Analytics Dashboard
❌ Blog
❌ Multi-language
❌ Multiple Admin Roles
❌ Advanced Animations
❌ Automated Tests
```

---

# 8. Priority Rule When Falling Behind

Deadline is fixed:

**30 Days.**

We never sacrifice:

```text
HTML/CSS fundamentals
JavaScript fundamentals
DOM
Fetch/API understanding
React fundamentals
State
Routing
CRUD
```

If we're behind schedule, remove in this order:

```text
1. Fancy visual polish
2. Complex animations
3. Extra Contact content
4. Multiple-image reordering
5. Advanced filters
6. Price display
```

Never remove:

```text
CRUD
Auth
Device status
At least one image
WhatsApp
Responsive public website
Deployment
```

---

# 9. Progress Checkpoints

## End of Day 6

**Static responsive website exists.**

## End of Day 12

**Vanilla JavaScript website talks to FastAPI.**

## End of Day 19

**React public website is functionally complete.**

## End of Day 23

**Real PostgreSQL CRUD works.**

## End of Day 26

**Admin/Auth/Images are complete.**

## End of Day 29

**Production deployment exists.**

## End of Day 30

**Website launched and accepted.**

---

# 10. Project Management Rule

Each day ends with:

```text
1. Run today's acceptance test.
2. Fix blocking bugs.
3. Git status.
4. Commit.
5. Push.
6. Update progress.
```

Suggested commit style:

```text
feat: build responsive device catalogue
feat: add device filters
feat: connect catalogue to FastAPI
feat: add admin device form
feat: implement device CRUD
feat: add admin authentication
feat: support image uploads
fix: handle missing device images
```

**No unfinished work gets silently carried forward.**

If a task isn't complete, it explicitly becomes the first task of the next day and a lower-priority future task gets cut.