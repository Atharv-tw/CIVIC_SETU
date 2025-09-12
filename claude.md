# claude.md

## 🧭 Project Overview: 
Crowdsourced Civic Issue Reporting & Resolution System

A mobile-first named platform named "CIVIC SETU" to empower **citizens of Jharkhand** to report civic issues with images/videos, **track complaint status**, and ensure **transparent municipal accountability**. 

Citizens use a **React Native mobile app**, while municipal staff operate via an **admin web dashboard**. The platform runs on **Node.js backend**, **MongoDB database**, and supports offline reporting, media uploads, automated routing, and analytics.

---

## 🛠️ Phase 1: MVP Setup

### 1. Tech Stack
- **Frontend (Mobile App)**: React Native
- **Backend**: Node.js (Express)
- **Database**: MongoDB (Mongoose ODM)
- **Media**: Cloudinary / AWS S3
- **Notifications**: Firebase Cloud Messaging (FCM)
- **Maps**: Google Maps or OpenStreetMap API
- **Auth**: JWT

### 2. Core Features to Build
#### For Citizens (React Native App):
- 📸 Capture photo/video, add text description
- 📍 Auto-GPS tagging
- 📶 Offline mode: save & queue reports for sync & Complaint status tracking with stage-wise updates
- 🔔 Push notifications for updates
- 🈯 Multilingual UI (Hindi, English, local languages)

#### For Admin Staff (Web Portal):
- 🔐 Role-based login (admin, supervisor, staff)
- 🗃️ Complaint dashboard with filters (status, category)
- 🗺️ Map view for complaints
- ✅ Assign/reassign tasks
- 📈 Analytics dashboard (basic)
- After completing task the admin can add comments to the complaint and can also add the status of the complaint.

---

## 🧑‍💻 Phase 2: Development Steps — Beginner Friendly

### 🌐 Step 1: Backend Folder Structure
```
civic-backend/
├── controllers/
├── models/
├── routes/
├── middleware/
├── utils/
├── .env
├── server.js
```
### 🌐 Step 2: Frontend Folder Structure
```
civic-frontend/
├── components/
├── screens/
├── routes/
├── assets/
├── reducers/
├── actions/
├── constants/
├── navigation/
├── utils/
├── styles/
├── types/
├── hooks/
├── services/
├── config/
├── index.js
├── App.js
├── package.json
├── .env
├── .gitignore
├── README.md
├── .eslintrc.js
├── .prettierrc.js
├── .babelrc
├── .env
```

### 🧱 Step 3: Backend Models (MongoDB)
#### User Model
```js
// models/User.js
userId, name, phone, language, createdAt, updatedAt, isActive, isDeleted, email, password, isVerified, isAdmin, isStaff, isSupervisor, address, city, state, pincode, latitude, longitude, profilePicture, role, createdBy, updatedBy
```
#### Report Model
```js
// models/Report.js
reportId, reporterId, title, description, category, location, status, createdAt, updatedAt, isActive, isDeleted, latitude, longitude, media, comments, createdBy, updatedBy, complaintStatus, complaintStatusUpdatedAt, complaintStatusUpdatedBy, complaintStatusUpdatedByRole, complaintStatusUpdatedByCommen
```
#### Media Model
```js
// models/Media.js
mediaId, reportId, type (image/video), url, thumbnailUrl, createdAt, updatedAt, isActive, isDeleted, createdBy, updatedBy, mediaType, mediaSize, mediaDuration
```

### 🚀 Step 4: Backend API Endpoints
```http
POST   /api/auth/register    --> Register user
POST   /api/auth/login       --> Login & get token
POST   /api/reports          --> Submit complaint (with media)
GET    /api/reports/:id      --> View complaint details
GET    /api/reports          --> List/filter complaints
PATCH  /api/reports/:id      --> Update status
```

### 📲 Step 5: React Native App Screens
- HomeScreen (List of complaints)
- CreateReportScreen (form + camera)
- ReportDetailScreen (status tracking)
- MyReportsScreen
- Login/RegisterScreen

Use AsyncStorage for local drafts + sync logic.
Use Expo Camera, Location APIs, and background tasks.

### 🧩 Step 6: Sync + Notifications
- Use FCM to send updates
- Track complaint stages: `submitted → acknowledged → assigned → resolved`
- Add offline queue using AsyncStorage

---

## ⚙️ Phase 3: Advanced System Features (Post MVP)

### 🔀 Auto-Routing Engine
- Phase 1: Rule-based (category + location → department)
- Phase 2: ML-enhanced (use metadata + AI)

### 🧵 Media Service
- Validate file type/size
- Generate thumbnails
- Store on S3 / Cloudinary
- Use CDN for fast delivery

### 🕵️ Admin Dashboard Features
- Role-based dashboard
- View reports with filters
- Assign tasks to field staff
- Comment system for reports
- SLA enforcement

---

## 🔒 Security & Compliance
- JWT + role-based access
- HTTPS enforced
- Rate limiting & anti-bot filters
- Encrypt PII & media links
- Audit logs for all actions
- Consent prompts for location/media

---

## 📊 Analytics & Reporting
- Use MongoDB aggregations for reporting
- Reports by region, status, category
- Export reports monthly
- Add hotspot detection via map clusters

---

## 🌍 Localization & Accessibility
- Use i18n framework (e.g., `i18next`)
- Hindi, English, tribal dialects
- Voice prompts (TTS) & large font toggle

---

## 📈 Monitoring & Deployment
- Use PM2 + Mongo Atlas for hosting
- GitHub + CI/CD workflows
- Uptime alerts via Cron + Status checks

---

## 🧪 Testing & QA
- Backend: Jest + Supertest
- React Native: Jest + Detox
- Use Postman for API testing

---

## 📅 Roadmap
| Month | Milestone |
|-------|-----------|
| 0–1   | Setup, login, DB, first report flow |
| 2     | Offline mode + media uploads |
| 3     | Admin dashboard + routing logic |
| 4–6   | Notifications + Analytics + Hotspot map |
| 6+    | ML routing + Government integrations |

---

## 🧩 Future Additions
- WhatsApp/SMS fallback reporting
- Aadhaar e-KYC integration
- Payment gateway for challans/fines
- NGO dashboard for issue verification

---

---

## 🚀 CURRENT PROJECT STATUS (Updated: January 2025)

### ✅ **COMPLETED FEATURES**

#### **Backend (Node.js + Express + MongoDB)**
- ✅ Complete REST API with authentication (JWT)
- ✅ User registration/login with role-based access
- ✅ Report CRUD operations with media upload (Cloudinary)
- ✅ Admin dashboard analytics endpoints
- ✅ Status management and assignment system
- ✅ Comment and feedback system
- ✅ Geographic queries and location handling

#### **Mobile App (React Native + Expo)**
- ✅ User authentication with persistent login
- ✅ Report creation with camera integration
- ✅ GPS location services with reverse geocoding
- ✅ Real-time report tracking and status updates
- ✅ Profile management with dynamic report counts
- ✅ My Reports screen with filtering
- ✅ Offline-ready with proper error handling

#### **Admin Dashboard (React + Material-UI)**
- ✅ Secure admin authentication
- ✅ Real-time dashboard with statistics
- ✅ Report management with status updates
- ✅ Staff assignment and task distribution
- ✅ Analytics and performance metrics
- ✅ Responsive design for multiple devices

### 🔧 **RECENT IMPROVEMENTS (January 2025)**

#### **Critical Bug Fixes Completed:**
1. **Navigation Flow** - Fixed logout functionality and report submission redirects
2. **Form Validation** - Improved location/address field validation logic
3. **Data Consistency** - Standardized report data across all components
4. **UI Alignment** - Fixed status chip alignment in admin dashboard
5. **Real-time Updates** - Dynamic report counts and consistent status display

#### **Architecture Enhancements:**
- **Centralized Configuration**: Created shared status configurations for consistency
- **Data Layer Improvements**: Standardized API response handling
- **Component Optimization**: Reduced code duplication with reusable utilities
- **Error Handling**: Enhanced user experience with better error messages

### 🌐 **DEPLOYMENT CONFIGURATION**

#### **Development URLs:**
- **Backend API**: http://localhost:5000
- **Admin Dashboard**: http://localhost:3000  
- **Mobile App**: http://localhost:8081 (Expo)

#### **Production Readiness:**
- ✅ Environment variables configured
- ✅ CORS properly setup for cross-origin requests
- ✅ Database connections optimized
- ✅ Media upload and storage working
- ✅ Authentication and authorization secure

### 📋 **REPORT CATEGORIES AVAILABLE**
```javascript
Categories: [
  'road_issue',      // Road Issues
  'water_supply',    // Water Supply  
  'electricity',     // Electricity
  'garbage',         // Garbage
  'drainage',        // Drainage
  'street_light',    // Street Light
  'traffic',         // Traffic
  'pollution',       // Pollution
  'encroachment',    // Encroachment
  'other'           // Other
]
```

### 🔄 **REPORT STATUS WORKFLOW**
```
submitted → acknowledged → assigned → in_progress → resolved
                                  ↓
                               rejected/closed
```

### 🗂️ **KEY FILES STRUCTURE**
```
CIVIC_SETU/
├── civic-backend/          # Node.js API Server
│   ├── models/            # MongoDB Models
│   ├── controllers/       # Business Logic
│   ├── routes/           # API Routes
│   └── middleware/       # Auth & Validation
├── civic-admin/          # React Admin Dashboard
│   ├── src/pages/       # Dashboard Pages
│   ├── src/constants/   # Shared Configuration
│   └── src/contexts/    # State Management
├── civic-mobile/        # React Native Mobile App
│   ├── src/screens/     # Mobile Screens
│   ├── src/services/    # API Integration
│   ├── src/constants/   # App Configuration
│   └── src/navigation/  # App Navigation
└── activity.log         # Development Activity Log
```

### 🛠️ **DEVELOPMENT COMMANDS**

#### **Start All Services:**
```bash
# Backend (Terminal 1)
cd civic-backend && npm run dev

# Admin Dashboard (Terminal 2) 
cd civic-admin && npm start

# Mobile App (Terminal 3)
cd civic-mobile && npm start
```

#### **Database & External Services:**
- **MongoDB**: Atlas cloud database configured
- **Cloudinary**: Media storage and image optimization
- **Expo**: Mobile app development and testing platform

### 🎯 **NEXT DEVELOPMENT PRIORITIES**

#### **Phase 1: Enhanced Features**
1. **Push Notifications** - Implement FCM for real-time updates
2. **Offline Mode** - Complete offline report creation and sync
3. **Map Integration** - Add interactive maps for report visualization
4. **Advanced Search** - Implement filtering and search capabilities

#### **Phase 2: Scale & Performance**
1. **Performance Optimization** - Implement caching and lazy loading
2. **Security Hardening** - Add rate limiting and advanced validation
3. **Analytics Dashboard** - Enhanced reporting and insights
4. **Multi-language Support** - Hindi and local language support

#### **Phase 3: Advanced Integrations**
1. **Government APIs** - Integration with municipal systems
2. **ML-based Routing** - Intelligent assignment of reports
3. **Citizen Engagement** - Community features and voting
4. **Mobile Web App** - PWA version for broader accessibility

### 📊 **TESTING & QUALITY ASSURANCE**

#### **Manual Testing Completed:**
- ✅ User registration and authentication flows
- ✅ Report creation with media upload
- ✅ Admin dashboard functionality  
- ✅ Status updates and notifications
- ✅ Cross-platform compatibility testing

#### **Automated Testing Setup:**
```bash
# Backend API Testing
cd civic-backend && npm test

# Frontend Unit Testing  
cd civic-admin && npm test
cd civic-mobile && npm test
```

### 🔍 **TROUBLESHOOTING GUIDE**

#### **Common Issues & Solutions:**
1. **CORS Errors**: Check allowed origins in `civic-backend/server.js`
2. **Database Connection**: Verify MongoDB Atlas connection string
3. **Mobile App Loading**: Ensure Expo CLI is updated
4. **Image Upload Issues**: Check Cloudinary configuration
5. **Authentication Problems**: Verify JWT secret keys

#### **Development Tips:**
- Use `activity.log` for tracking changes and debugging
- Check browser console for API errors
- Use React Native debugger for mobile issues
- Monitor backend logs for server-side problems

---

## 📞 **SUPPORT & DOCUMENTATION**

For detailed development guidance, refer to:
- `activity.log` - Recent changes and bug fixes
- Component documentation in respective `/src` folders
- API documentation via Postman collections
- Database schema in `/models` directory

Need help understanding or implementing any specific part? Just ask `/explain <section>` or `/build <feature>` to get a step-by-step tutorial.