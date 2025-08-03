# Project Architecture & File Structure Guide

**Target:** Hackathon Development (48 Hours)\
**Focus:** Agility, Simplicity, and Rapid Prototyping\
**Architecture:** Progressive Web App with AI/ML Backend

***

## 🏗️ Project Overview

This guide provides a streamlined file structure for building an AI-powered personalized learning platform optimized for hackathon development. The architecture prioritizes rapid development while maintaining scalability and clean separation of concerns.

## 📁 Recommended File Structure

```
hackathon-project/
├── README.md
├── package.json
├── .env.example
├── .gitignore
├── vercel.json                 # Deployment configuration
│
├── public/                     # Static assets
│   ├── manifest.json          # PWA manifest
│   ├── sw.js                  # Service worker for offline
│   ├── icons/                 # App icons
│   └── assets/                # Images, fonts, etc.
│
├── src/                       # Main application source
│   ├── index.html             # Entry point
│   ├── main.js               # Application bootstrap
│   ├── style.css             # Global styles
│   │
│   ├── components/           # Reusable UI components
│   │   ├── common/          # Shared components
│   │   │   ├── Button.js
│   │   │   ├── Modal.js
│   │   │   ├── Loading.js
│   │   │   └── Navigation.js
│   │   │
│   │   ├── teacher/         # Teacher-specific components
│   │   │   ├── Dashboard.js
│   │   │   ├── ContentReview.js
│   │   │   ├── AILiteracy.js
│   │   │   └── Analytics.js
│   │   │
│   │   └── student/         # Student-specific components
│   │       ├── LearningInterface.js
│   │       ├── ContentViewer.js
│   │       └── ProgressTracker.js
│   │
│   ├── pages/               # Main application pages
│   │   ├── HomePage.js
│   │   ├── TeacherDashboard.js
│   │   ├── StudentPortal.js
│   │   ├── AITraining.js
│   │   └── Analytics.js
│   │
│   ├── services/            # Business logic & API calls
│   │   ├── api.js          # API configuration
│   │   ├── auth.js         # Authentication
│   │   ├── contentAI.js    # EPIC 1: Content personalization
│   │   ├── analytics.js    # EPIC 3: Progress analytics
│   │   └── offline.js      # EPIC 4: Offline functionality
│   │
│   ├── utils/               # Helper functions
│   │   ├── constants.js
│   │   ├── validators.js
│   │   ├── formatters.js
│   │   └── storage.js
│   │
│   └── data/                # Mock data & configurations
│       ├── mockContent.js
│       ├── userProfiles.js
│       └── aiPrompts.js
│
├── api/                     # Backend API (Serverless functions)
│   ├── content/
│   │   ├── personalize.js   # EPIC 1: AI content adaptation
│   │   ├── ingest.js       # Content ingestion
│   │   └── analyze.js      # Content analysis
│   │
│   ├── analytics/
│   │   ├── progress.js     # EPIC 3: Student progress
│   │   ├── engagement.js   # Engagement metrics
│   │   └── reports.js      # Export functionality
│   │
│   ├── training/
│   │   ├── modules.js      # EPIC 2: AI literacy modules
│   │   ├── progress.js     # Teacher progress tracking
│   │   └── community.js    # Forum/chat features
│   │
│   └── auth/
│       ├── login.js
│       └── validate.js
│
├── tests/                   # Testing (minimal for hackathon)
│   ├── components/
│   └── services/
│
└── docs/                    # Documentation
    ├── API.md
    ├── DEPLOYMENT.md
    └── FEATURES.md
```

## 🎯 EPIC Implementation Mapping

### EPIC 1: AI-Powered Content Personalization

**Files:** `src/services/contentAI.js`, `api/content/`, `src/components/teacher/ContentReview.js`

```javascript
// src/services/contentAI.js
export class ContentPersonalization {
  async personalizeContent(content, studentProfile) {
    // Rule-based personalization logic
    // API call to backend for AI processing
  }
  
  async ingestContent(rawContent) {
    // Content parsing and preparation
  }
}
```

### EPIC 2: Interactive Teacher AI Literacy

**Files:** `src/pages/AITraining.js`, `api/training/`, `src/components/teacher/AILiteracy.js`

```javascript
// src/pages/AITraining.js
export function AITrainingModule() {
  // Gamified learning interface
  // Progress tracking
  // Interactive tutorials
}
```

### EPIC 3: Student Progress Analytics

**Files:** `src/pages/Analytics.js`, `api/analytics/`, `src/components/teacher/Analytics.js`

```javascript
// src/services/analytics.js
export class AnalyticsService {
  async getStudentProgress(classId) {
    // Progress visualization data
  }
  
  async generateReports(filters) {
    // Exportable reports
  }
}
```

### EPIC 4: Accessible Interface & Offline Support

**Files:** `public/sw.js`, `src/services/offline.js`, responsive CSS

```javascript
// public/sw.js
self.addEventListener('fetch', (event) => {
  // Offline-first caching strategy
});
```

## 🚀 Development Workflow

### Phase 1: Foundation (Hours 1-8)

1. **Setup & Configuration**

   ```bash
   npm init -y
   npm install vite react tailwindcss
   # Setup basic PWA structure
   ```

2. **Core Components**

   * Navigation system
   * Authentication flow
   * Basic routing
   * Responsive layout

### Phase 2: EPIC Implementation (Hours 9-32)

1. **EPIC 4 First** (Infrastructure)

   * PWA setup with offline capabilities
   * Responsive design system
   * Basic UI components

2. **EPIC 1** (Core Value)

   * Content ingestion system
   * Basic personalization rules
   * Teacher review dashboard

3. **EPIC 2** (Differentiation)

   * AI literacy training modules
   * Interactive tutorials
   * Progress tracking

4. **EPIC 3** (Analytics)

   * Progress visualization
   * Basic analytics dashboard
   * Export functionality

### Phase 3: Integration & Polish (Hours 33-48)

* System integration testing
* UI/UX refinements
* Demo preparation
* Documentation updates

## 🛠️ Technology Stack

### Frontend

* **Framework:** Vanilla JS + Vite (for speed) or React (if preferred)
* **Styling:** Tailwind CSS
* **PWA:** Workbox for service workers
* **Charts:** Chart.js for analytics
* **State:** LocalStorage + simple state management

### Backend

* **Runtime:** Vercel Serverless Functions (Node.js)
* **AI/ML:** OpenAI API or Hugging Face API
* **Database:** Vercel KV (Redis) for session data
* **Storage:** Vercel Blob for content files

### Development Tools

* **IDE:** Cursor with AI assistance
* **Bundler:** Vite for fast development
* **Deployment:** Vercel (zero-config)
* **Version Control:** Git with GitHub

## 📱 PWA Configuration

### manifest.json

```json
{
  "name": "AI-Powered Learning Platform",
  "short_name": "AILearning",
  "description": "Personalized learning for high school students",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#3498db",
  "icons": [
    {
      "src": "/icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}
```

## 🔧 Key Configuration Files

### package.json (Essential Dependencies)

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "chart.js": "^4.4.0",
    "tailwindcss": "^3.3.0"
  },
  "devDependencies": {
    "vite": "^4.4.0",
    "@vitejs/plugin-react": "^4.0.0"
  }
}
```

### vercel.json (Deployment)

```json
{
  "functions": {
    "api/**/*.js": {
      "runtime": "nodejs18.x"
    }
  },
  "rewrites": [
    {
      "source": "/((?!api/).*)",
      "destination": "/index.html"
    }
  ]
}
```

## 🎨 Styling Strategy

### Tailwind Configuration

* Mobile-first responsive design
* Custom color palette for education
* Accessibility-focused utilities
* Dark mode support (optional)

### Component Structure

```javascript
// Example component structure
export function TeacherDashboard() {
  return (
    <div className="min-h-screen bg-gray-50">
      <Navigation />
      <main className="container mx-auto px-4 py-8">
        <ContentPersonalization />
        <ProgressAnalytics />
        <AILiteracyModules />
      </main>
    </div>
  );
}
```

## 🔄 Data Flow Architecture

```
User Input -> Component -> Service -> API -> AI Processing -> Database -> Response -> UI Update
```

### State Management

* **Local State:** React useState for component state
* **Global State:** Context API for user authentication
* **Persistent State:** LocalStorage for offline data
* **Cache:** Service Worker cache for content

## 📊 Analytics Implementation

### Progress Tracking

```javascript
// Simple analytics structure
const studentProgress = {
  studentId: 'string',
  contentId: 'string',
  completionRate: 'number',
  engagementScore: 'number',
  strugglingAreas: 'array',
  timestamp: 'date'
};
```

## 🚨 Hackathon Priorities

### Must-Have (Core MVPs)

1. ✅ Working content personalization demo
2. ✅ Teacher AI literacy module (basic)
3. ✅ Progress visualization dashboard
4. ✅ Responsive offline-capable interface

### Nice-to-Have (If Time Permits)

* Advanced AI personalization
* Real-time collaboration features
* Advanced analytics exports
* Enhanced gamification

### Demo Preparation

* **Folder:** `/demo/`
* **Files:** `demo-script.md`, `demo-data.json`, `screenshots/`

## 🔐 Security Considerations

### Environment Variables (.env)

```
OPENAI_API_KEY=your_key_here
VERCEL_KV_URL=your_kv_url
VERCEL_KV_REST_API_URL=your_api_url
VERCEL_KV_REST_API_TOKEN=your_token
```

### Data Privacy

* No real student data in hackathon
* Mock data with privacy-first design
* FERPA-compliant data structure

***

## 🎯 Getting Started Checklist
* [ ] Clone repository structure
* [ ] Install dependencies (`npm install`)
* [ ] Configure environment variables
* [ ] Setup Vercel deployment
* [ ] Implement EPIC 4 (foundation)
* [ ] Build EPIC 1 (core value)
* [ ] Develop EPIC 2 (differentiation)
* [ ] Create EPIC 3 (analytics)
* [ ] Integration testing
* [ ] Demo preparation

## 🤝 Development Tips for Cursor

1. **Use AI Assistance:** Leverage Cursor's AI for boilerplate code generation
2. **Component-First:** Build reusable components early
3. **API-Driven:** Design API endpoints before frontend implementation
4. **Mobile-First:** Start with mobile layouts, expand to desktop
5. **Iterate Fast:** Focus on working prototypes over perfect code

***

**Ready to build? Start with the foundation and work your way up through the EPICs! 🚀**
