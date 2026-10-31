# Smart Campus Resources & Lab Management System

**Institution:** Anantha Lakshmi Institute of Technology and Sciences (ALITS)  
**Campus Platform:** Autonomous Engineering College Academic & Laboratory Infrastructure  
**Stack:** Vanilla HTML5, CSS3, JavaScript, Node.js, Express.js, Supabase PostgreSQL & Storage

---

## 🌟 Overview & Key Capabilities

1. **Highlight Slider (Five Carousel Slides):**
   - Five comprehensive campus highlights with smooth automatic sliding every 4.5 seconds.
   - Interactive dots, prev/next arrows, touch swiping gestures on mobile, hover-to-pause, and reduced-motion accessibility.
   - Faculty management panel to update slides, descriptions, links, and banners.

2. **Smart Campus Assistant (Right-Corner Chatbot):**
   - Floating assistant on every page.
   - Quick-reply action chips for Study Materials, Timetables, Latest Updates, PYQs, Lab Facilities, and Helpdesk Support.
   - Guided branch & semester selection for students.
   - Adheres strictly to security: never leaks faculty passwords, private keys, or admin records.

3. **Academic PDF & Notes Management:**
   - Multi-department filtering across 7 branches: CSE, CSM (AI & ML), CSD (Data Science), ECE, EEE, Mechanical, Civil.
   - Semesters 1 through 8 support.
   - Categories: Lecture Notes, Unit-wise Notes, Previous Question Papers (PYQs), Lab Manuals, Assignments, and Reference Materials.
   - PDF preview modal and fast direct downloads.
   - Faculty upload with file size validation (max 50 MB) and progress bar backed by Supabase Storage & PostgreSQL metadata.

4. **College & University Announcements:**
   - Dedicated announcements board with category filtering: University Notifications, Examination Updates, Results, Hall Tickets, Academic Calendars, Placements, and Technical Events.
   - Verified issuing source tags and official link verification.

5. **Laboratory & Facilities Infrastructure:**
   - Live availability tracking (`Available`, `In Use`, `Maintenance`).
   - Detailed equipment lists, capacity counters, and hardware/software configurations.

6. **Classrooms & Smart Board Management:**
   - Classroom locations across campus blocks (Sir Visvesvaraya Block, Dr. APJ Abdul Kalam Tech Block, etc.).
   - Laser projector and interactive smart touch panel tracking.

7. **Timetables & Conflict Detection:**
   - Filter weekly class schedules by branch, semester, and section.
   - Time conflict detection prevents overlapping room and lab allocations.

8. **Secure Faculty Authentication (One Shared Password):**
   - Master Faculty password verification performed server-side with bcrypt.
   - Protected with tamper-proof HTTP-only cookies and brute-force rate-limiting.
   - Authorization middleware protects all mutations (uploads, edits, deletions).

---

## 📁 Project Structure

```
smart-campus-management/
│
├── public/                          # Public Frontend Assets
│   ├── index.html                   # Homepage with 5-slide carousel & notice feed
│   ├── academic-materials.html      # Study materials, PYQs & notes viewer
│   ├── laboratories.html            # Lab directory & equipment count
│   ├── classrooms.html              # Smart classrooms & projector status
│   ├── equipment.html               # Hardware & projector inventory
│   ├── timetable.html               # Weekly class schedule
│   ├── updates.html                 # College & university notice board
│   ├── faculty-login.html           # Single password faculty authentication
│   ├── faculty-dashboard.html       # Management portal (CRUD for resources)
│   ├── css/
│   │   ├── style.css                # Dark green, gold & academic theme
│   │   ├── responsive.css           # Mobile & tablet responsiveness
│   │   └── chatbot.css              # Smart Campus Assistant UI
│   ├── js/
│   │   ├── main.js                  # Global navigation & live metrics
│   │   ├── carousel.js              # Five-image highlight slider logic
│   │   ├── chatbot.js               # Interactive guided assistant
│   │   ├── academic-materials.js    # PDF filters, search & preview modal
│   │   ├── updates.js               # Announcements feed & filters
│   │   ├── facilities.js            # Labs, classrooms & equipment logic
│   │   ├── timetable.js             # Timetable schedule rendering
│   │   ├── faculty-login.js         # Login form & rate limit handler
│   │   └── faculty-dashboard.js     # Faculty CRUD operations & uploads
│   └── assets/
│       ├── images/                  # SVGs for logo & 5 highlight slides
│       └── uploads/                 # Storage for sample academic PDFs
│
├── src/                             # Backend Application
│   ├── server.js                    # Express app configuration & server
│   ├── config/
│   │   └── supabase.js              # Supabase client & local DB fallback
│   ├── middleware/
│   │   ├── auth.js                  # Faculty session verification & JWT
│   │   └── rate-limit.js            # Brute-force protection
│   ├── routes/
│   │   ├── auth.routes.js           # Login, logout & session status
│   │   ├── materials.routes.js      # PDF upload, filter, delete
│   │   ├── updates.routes.js        # Announcements CRUD
│   │   ├── facilities.routes.js     # Labs, classrooms & equipment
│   │   ├── timetable.routes.js      # Timetable allocation & clash check
│   │   └── carousel.routes.js       # Highlight slides management
│   └── services/
│       ├── storage.service.js       # Supabase Storage bucket management
│       └── updates.service.js       # Verified circulars & notices
│
├── supabase/
│   ├── schema.sql                   # Database schema & initial seed data
│   └── policies.sql                 # Row Level Security (RLS) & buckets
│
├── tests/
│   └── test-runner.js               # Automated system verification test
│
├── .env.example                     # Environment template
├── .env                             # Local active configuration
├── .gitignore
├── package.json
└── README.md
```

---

## 🚀 Quick Start Guide

### Step 1: Open in VS Code
Open the project directory in Visual Studio Code:
```bas
```

### Step 2: Install Node.js Dependencies
Run in your terminal inside the project directory:
```bash
npm install
```

### Step 3: Run the Application
Start the Node.js server:

npm start
```
The server will start on:
**[http://localhost:5000](http://localhost:5000)**

---

## 🔐 Faculty Authentication Credentials

- **Faculty Login Page:** [http://localhost:5000/faculty-login.html](http://localhost:5000/faculty-login.html)
- **Default Master Password:** `AlitsFaculty@2025`

> **Note:** The password is verified server-side with bcrypt. To change the password, update `FACULTY_PASSWORD` and generate a new hash in your `.env` file.

---

## 🗄️ Supabase PostgreSQL & Storage Setup

1. Create a free project on [Supabase.com](https://supabase.com).
2. Go to **SQL Editor** in your Supabase dashboard:
   - Run the script located in `supabase/schema.sql` to create all tables and initial seed data.
   - Run the script in `supabase/policies.sql` to configure Row Level Security (RLS) and storage buckets (`academic-materials` and `campus-assets`).
3. Retrieve your credentials from **Project Settings → API**:
   - Project URL (`SUPABASE_URL`)
   - `anon` Public Key (`SUPABASE_ANON_KEY`)
   - `service_role` Secret Key (`SUPABASE_SERVICE_ROLE_KEY`)
4. Paste these values into your `.env` file:
   ```env
   SUPABASE_URL=https://your-project-id.supabase.co
   SUPABASE_ANON_KEY=your-anon-public-key-here
   SUPABASE_SERVICE_ROLE_KEY=your-service-role-secret-key-here
   ```
5. Restart your server (`npm start`). The system automatically transitions from the local fallback to your live Supabase cloud database and storage!

---

## 🧪 Testing

To run the automated verification test:
```bash
npm test
```
Verifies all HTML views, stylesheets, JavaScript modules, SVG illustrations, and security hashes.

---

## 🌐 Production Deployment

- **Node.js Hosts:** Can be deployed to Render, Railway, DigitalOcean, Heroku, or AWS Elastic Beanstalk.
- Set environment variables (`PORT`, `NODE_ENV=production`, `SESSION_SECRET`, `FACULTY_PASSWORD_HASH`, `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`).
- For HTTPS, secure cookies are automatically enabled.
