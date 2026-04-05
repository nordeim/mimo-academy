iTrust Academy v2 - Project Overview                                                                                                                                                                                                      
                                                                                                                                                                                                                                          
What is this project?                                                                                                                                                                                                                     
                                                                                                                                                                                                                                          
iTrust Academy is a production-ready enterprise IT training and certification platform. It serves IT professionals in the Asia-Pacific region, offering courses from 4 major vendors (SolarWinds, Securden, Quest, Ivanti). The platform  
has both a React frontend and a Django REST API backend.
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
Tech Stack
                                                                                                                                                                                                                                          
┌──────────────────┬─────────────────────────────────────────────────┐
│      Layer       │                   Technology                    │
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ Frontend         │ React 19 + TypeScript + Tailwind CSS v4 + Vite  │
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ Backend          │ Django 6.0 + Django REST Framework + Python 3.x │                                                                                                                                                                    
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ UI Components    │ Radix UI primitives + Framer Motion animations  │                                                                                                                                                                    
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ State Management │ Zustand (auth), React Query (server state)      │
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ Database         │ SQLite (development) / PostgreSQL (production)  │
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ Testing          │ Vitest (unit), Playwright (E2E)                 │
├──────────────────┼─────────────────────────────────────────────────┤                                                                                                                                                                    
│ Auth             │ JWT with token refresh                          │
└──────────────────┴─────────────────────────────────────────────────┘                                                                                                                                                                    
                
---                                                                                                                                                                                                                                       
Project Structure
                 
/home/project/iTrust-Academy/mimo-v2/
├── frontend/                    # React 19 + Vite frontend                                                                                                                                                                               
│   ├── src/                                                                                                                                                                                                                              
│   │   ├── app/                # Main app component & routing                                                                                                                                                                            
│   │   ├── components/                                                                                                                                                                                                                   
│   │   │   ├── sections/       # Page sections (Hero, Catalog, etc.)                                                                                                                                                                     
│   │   │   ├── layout/         # Header, Footer, Container                                                                                                                                                                               
│   │   │   ├── ui/             # Reusable UI primitives                                                                                                                                                                                  
│   │   │   ├── forms/          # Login/Register modals                                                                                                                                                                                   
│   │   │   └── pages/          # Route-level page components                                                                                                                                                                             
│   │   ├── hooks/              # useAuth, useCourses, useCategories                                                                                                                                                                      
│   │   ├── lib/                # Utilities, constants, API client                                                                                                                                                                        
│   │   ├── data/               # Static course data                                                                                                                                                                                      
│   │   ├── styles/             # CSS, animation variants                                                                                                                                                                                 
│   │   └── types/              # TypeScript type definitions                                                                                                                                                                             
│   ├── public/                 # Static assets (favicon, images)                                                                                                                                                                         
│   ├── screenshots/            # E2E test evidence                                                                                                                                                                                       
│   └── tests/                  # Unit tests (14 tests passing)                                                                                                                                                                           
│                                                                                                                                                                                                                                         
├── backend/                     # Django REST API                                                                                                                                                                                        
│   ├── server/                 # Django project settings                                                                                                                                                                                 
│   │   ├── settings.py         # Main settings with JWT auth                                                                                                                                                                             
│   │   ├── urls.py             # API routes                                                                                                                                                                                              
│   │   └── wsgi.py                                                                                                                                                                                                                       
│   ├── api/                    # Views, serializers, models                                                                                                                                                                              
│   │   ├── models/             # Course, Category, Auth models                                                                                                                                                                           
│   │   ├── serializers/        # DRF serializers                                                                                                                                                                                         
│   │   ├── views/              # API views (Login, Register, Courses)                                                                                                                                                                    
│   │   └── management/         # Custom management commands                                                                                                                                                                              
│   ├── scripts/                # Utility scripts (init_db, test)                                                                                                                                                                         
│   ├── logs/                   # Application logs                                                                                                                                                                                        
│   ├── db/                     # SQLite database                                                                                                                                                                                         
│   └── requirements.txt        # Python dependencies                                                                                                                                                                                     
│                                                                                                                                                                                                                                         
├── docs/                       # Documentation & diagrams                                                                                                                                                                                
├── docs-build/                 # Built documentation                                                                                                                                                                                     
└── memory/                     # Project memory (CLAUDE.md, etc.)                                                                                                                                                                        
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
Key Features                                                                                                                                                                                                                              
                                                                                                                                                                                                                                          
Frontend (React)
- 8-page routing with react-router-dom (Home, Courses, Course Detail, User Dashboard, About, FAQ, Privacy, Terms, 404)                                                                                                                    
- Hero section with Framer Motion animations                                                                                                                                                                                              
- Course catalog with filtering by vendor/category, search with debouncing
- Course detail pages with tabbed navigation (Overview, Curriculum, Instructor, Certification)                                                                                                                                            
- User dashboard with achievements and quick actions                                                                                                                                                                                      
- Authentication UI (login/register modals) with Zod validation                                                                                                                                                                           
- Contact modals (Consultation, Demo, Sales)                                                                                                                                                                                              
- "Coming Soon" modal for placeholder links                                                                                                                                                                                               
- Responsive design (mobile-first with hamburger menu)                                                                                                                                                                                    
- Full API integration with Django backend                                                                                                                                                                                                
- JWT token handling with automatic refresh                                                                                                                                                                                               
- Social media links with security attributes                                                                                                                                                                                             
- Skip-to-content accessibility link and WCAG 2.1 compliant dialogs                                                                                                                                                                       
                                                                                                                                                                                                                                          
Backend (Django)                                                                                                                                                                                                                          
- Django REST Framework API with JWT authentication                                                                                                                                                                                       
- User registration/login/logout with token-based auth                                                                                                                                                                                    
- Course and Category models with full CRUD                                                                                                                                                                                               
- SQLite database with migration support                                                                                                                                                                                                  
- CORS configured for frontend integration                                                                                                                                                                                                
- Admin interface for content management                                                                                                                                                                                                  
- Logging system for API requests                                                                                                                                                                                                         
- JSON Web Token (JWT) authentication with refresh tokens                                                                                                                                                                                 
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
Current Status                                                                                                                                                                                                                            
                                                                                                                                                                                                                                          
┌─────────────────┬───────────────────────┐
│     Metric      │        Status         │                                                                                                                                                                                               
├─────────────────┼───────────────────────┤
│ Unit Tests      │ 14/14 passing         │                                                                                                                                                                                               
├─────────────────┼───────────────────────┤
│ E2E Tests       │ 33/33 passing (100%)  │                                                                                                                                                                                               
├─────────────────┼───────────────────────┤                                                                                                                                                                                               
│ QA Validation   │ 47/47 elements (100%) │                                                                                                                                                                                               
├─────────────────┼───────────────────────┤                                                                                                                                                                                               
│ Lint            │ 0 errors              │
├─────────────────┼───────────────────────┤                                                                                                                                                                                               
│ Build Time      │ ~1.5 seconds          │
├─────────────────┼───────────────────────┤                                                                                                                                                                                               
│ UI/UX Usability │ 100%                  │
└─────────────────┴───────────────────────┘                                                                                                                                                                                               
                
---                                                                                                                                                                                                                                       
Key Configuration Files
                                                                                                                                                                                                                                          
┌──────────────────────────────┬──────────────────────────────────────────┐
│             File             │                 Purpose                  │                                                                                                                                                               
├──────────────────────────────┼──────────────────────────────────────────┤
│ frontend/src/app/app.tsx     │ Main app component with all sections     │
├──────────────────────────────┼──────────────────────────────────────────┤
│ frontend/src/app/globals.css │ Tailwind v4 theme tokens & CSS variables │                                                                                                                                                               
├──────────────────────────────┼──────────────────────────────────────────┤                                                                                                                                                               
│ frontend/vite.config.ts      │ Vite config with API proxy (port 5174)   │                                                                                                                                                               
├──────────────────────────────┼──────────────────────────────────────────┤                                                                                                                                                               
│ frontend/tsconfig.json       │ TypeScript strict mode config            │
├──────────────────────────────┼──────────────────────────────────────────┤                                                                                                                                                               
│ backend/server/settings.py   │ Django settings with JWT auth            │
├──────────────────────────────┼──────────────────────────────────────────┤                                                                                                                                                               
│ backend/api/urls.py          │ Django REST API routes                   │
├──────────────────────────────┼──────────────────────────────────────────┤                                                                                                                                                               
│ backend/requirements.txt     │ Python dependencies                      │
└──────────────────────────────┴──────────────────────────────────────────┘                                                                                                                                                               
                
---                                                                                                                                                                                                                                       
Development Commands
                                                                                                                                                                                                                                          
Frontend:
cd frontend                                                                                                                                                                                                                               
npm run dev          # Start Vite dev server (port 5174)
npm run build        # Production build                                                                                                                                                                                                   
npm run lint         # ESLint                                                                                                                                                                                                             
npm test             # Vitest unit tests                                                                                                                                                                                                  
npm run preview      # Preview production build                                                                                                                                                                                           
                                                                                                                                                                                                                                          
Backend:                                                                                                                                                                                                                                  
cd backend                                                                                                                                                                                                                                
python manage.py runserver    # Django dev server (port 8000)                                                                                                                                                                             
python manage.py migrate      # Run migrations                                                                                                                                                                                            
python manage.py init_db      # Initialize database with seed data                                                                                                                                                                        
python test_register_login.py # Run auth tests                                                                                                                                                                                            
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
Design System                                                                                                                                                                                                                             
                                                                                                                                                                                                                                          
- Primary Color: Burnt orange (#f27a1a) - brand identity                                                                                                                                                                                  
- Typography: DM Sans (body), Space Mono (monospace)                                                                                                                                                                                      
- Spacing: Standard Tailwind with container max-w-7xl                                                                                                                                                                                     
- Components: Built on Radix UI primitives, styled with Tailwind                                                                                                                                                                          
- Animations: Framer Motion for entrances, hover effects, micro-interactions                                                                                                                                                              
- Philosophy: Intentional minimalism, anti-generic, avant-garde UI design                                                                                                                                                                 
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
Dependencies Summary                                                                                                                                                                                                                      
                                                                                                                                                                                                                                          
Frontend: React 19, TypeScript 5.9, Tailwind CSS v4, Vite 8, Framer Motion, Zod, Zustand, React Query, Axios, Radix UI primitives, Lucide icons
                                                                                                                                                                                                                                          
Backend: Django 6.0, Django REST Framework, djangorestframework-simplejwt (JWT), django-cors-headers, SQLite/PostgreSQL                                                                                                                   
                                                                                                                                                                                                                                          
---                                                                                                                                                                                                                                       
This is a mature, production-ready full-stack application with comprehensive testing, authentication, API integration, and a distinctive UI design philosophy focused on intentional minimalism and accessibility.

● The CLAUDE.md file has been created. Here's what I found and distilled:                                                                                                                                                                   
                                                                                                                                                                                                                                            
  Key Changes Made                                                                                                                                                                                                                          
   
  Removed from existing CLAUDE.md:                                                                                                                                                                                                          
  - Obvious advice ("provide helpful error messages", "write unit tests")
  - Generic development practices                                                                                                                                                                                                           
  - Exhaustive component lists (easily discoverable via ls)
  - Repetitive sections                                                                                                                                                                                                                     
  - "Tips and Tricks" that stated the obvious                                                                                                                                                                                               
                                                                                                                                                                                                                                            
  Kept and refined:                                                                                                                                                                                                                         
  - Specific command references (exact npm/Django commands)                                                                                                                                                                                 
  - Architecture patterns requiring reading multiple files (CVA variants, data flow)                                                                                                                                                        
  - Critical constraints learned from codebase (export rules, form validation quirks, accessibility requirements)                                                                                                                           
  - Design philosophy from .cursorrules (Intentional Minimalism, Library Discipline)                                                                                                                                                        
                                                                                                                                                                                                                                            
  New CLAUDE.md Highlights                                                                                                                                                                                                                  
                                                                                                                                                                                                                                            
  ┌──────────────────────┬──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┐                                                                   
  │       Section        │                                                                   Key Info                                                                   │                                                                   
  ├──────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤                                                                   
  │ Commands             │ Frontend: npm run dev, npm run build, npm test, npx vitest run <file> Backend: python manage.py runserver, python manage.py init_db          │
  ├──────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤                                                                   
  │ Architecture         │ Component hierarchy: pages/ → sections/ → layout/ → ui/ Data flow: Django → apiClient (Axios+JWT) → React Query → UI                         │                                                                   
  ├──────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤                                                                   
  │ Key Patterns         │ CVA variants in ui/variants.ts, Framer Motion variants in lib/animations.ts, cn() utility for class merging                                  │                                                                   
  ├──────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┤                                                                   
  │ Critical Constraints │ Never export constants from component files (fast-refresh), Zod forms need empty string defaults, Dialog requires Title+Description for a11y │
  └──────────────────────┴──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────┘                                                                   
                  
  The file is now ~85 lines (down from ~600+), containing only hard-won, non-obvious knowledge that requires reading multiple files to discover. 
