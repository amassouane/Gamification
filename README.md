# Gamified Communication Skills LMS

A gamified learning platform that helps students and young job-seekers build **professional communication skills**, written and oral, through hands-on exercises, XP, levels, badges, streaks and peer feedback.

The project is inspired by the **Injaz Al-Maghrib "Steer Your Career"** program. It turns its classroom activities (such as the analog "CV Game") into interactive digital exercises.

## ✨ Features

### Exercises
| Exercise | What the learner does | How it's scored |
|----------|----------------------|-----------------|
| **CV Game** | Drag and drop CV sections (contact, profile, experience, education, skills) into the right order | % of sections in the correct position; perfect score gives a 1.5× XP bonus |
| **Email Pro** | Write a professional email (job application, follow-up, networking) for a given scenario | Auto-scored on tone, structure and grammar; ≥ 90% gives a 1.2× XP bonus |
| **Video Pitch** | Record and submit an elevator pitch or interview answer | Reviewed by peers |
| **Quiz Game** | Multiple-choice questions on email etiquette, CVs, presentations and interviews (e.g. the STAR method) | % of correct answers |

### Gamification
- **XP & levels**: every exercise awards XP; reaching the next level requires `level × 100` XP.
- **Badges**: 35 achievements, awarded automatically for levels, XP milestones, streaks, written/oral skills and peer reviews.
- **Daily streaks**: consecutive days of activity are tracked and rewarded.
- **Leaderboard**: learners are ranked by XP.
- **Peer review**: learners rate each other's video pitches on a 1–5 rubric (clarity, confidence, structure, persuasiveness) and leave written feedback.

### Courses
10 courses across written and oral communication, such as CV & Resume Mastery, Advanced Email Etiquette, Elevator Pitch Excellence, Job Interview Communication and Presentation Skills Fundamentals.

## 🛠️ Tech Stack

- **Backend:** Laravel 11 (PHP 8.2+), Laravel Sanctum, REST API under `/api/v1`
- **Frontend:** React 19 + React Router, Tailwind CSS, Vite
- **Database:** SQLite by default (MySQL/PostgreSQL also work via `.env`)

## 🚀 Getting Started

### Requirements
- PHP 8.2+ and Composer
- Node.js 18+ and npm

### Installation
```bash
git clone https://github.com/amassouane/Gamification.git
cd Gamification

composer install
npm install

cp .env.example .env
php artisan key:generate

touch database/database.sqlite      # on Windows: type nul > database\database.sqlite
php artisan migrate --seed          # create tables and load demo data
```

### Running the app
Run each of these in its own terminal:
```bash
php artisan serve     # Laravel backend at http://127.0.0.1:8000
npm run dev           # Vite dev server for the React frontend
```
Or start everything at once with `composer run dev`.

Then open **http://127.0.0.1:8000**.

### Running tests
```bash
php artisan test
```

## 🔑 Demo Accounts

The seeders create 10 demo users. All passwords are `password`.

| Email | Level | Profile |
|-------|-------|---------|
| admin@communicationlms.com | 1 | Administrator |
| student@example.com | 4 | Active learner, 5-day streak |
| maria.garcia@example.com | 6 | Advanced learner |
| fatima.rashid@example.com | 8 | Power user, 20-day streak |
| james.wilson@example.com | 1 | Beginner |

The seed data also includes 35 badges, 10 courses, 17 exercises, 38 quiz questions, sample submissions and 23 peer reviews.

## 📡 API Overview

All endpoints are prefixed with `/api/v1`.

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/dashboard` | User stats, XP, level, streak, badges |
| GET | `/leaderboard` | Learners ranked by XP |
| GET | `/courses` · `/courses/{id}` | List and view courses |
| POST | `/courses/{id}/enroll` | Enroll in a course |
| GET | `/quizzes/{id}` | Get a quiz |
| POST | `/quizzes/{id}/start` · `/quizzes/{id}/submit` | Start or submit a quiz |
| POST | `/exercises/{id}/cv/submit` | Submit a CV Game answer |
| POST | `/exercises/{id}/email/submit` | Submit an email exercise |
| POST | `/pitches/{id}/submit` | Submit a video pitch |
| GET | `/pitches/for-review` · `/pitches/my-pitches` | Pitches to review / my pitches |
| POST | `/pitches/{id}/review` | Submit a peer review |

## 📁 Project Structure

```
app/
├── Http/Controllers/Api/   # REST API controllers
├── Models/                 # Eloquent models (User, Course, Quiz, Badge, VideoPitch, ...)
└── Services/               # Business logic: GamificationService, QuizService,
                            # CVExerciseService, EmailExerciseService, VideoPitchService
database/
├── migrations/             # Database schema
└── seeders/                # Demo data
resources/js/
├── components/             # App shell, Header, StatsCard, XPProgressBar
└── pages/                  # Dashboard, Leaderboard, Badges, CVGame, EmailPro,
                            # QuizGame, VideoPitch, PeerReview
routes/
├── api.php                 # API routes
└── web.php                 # Serves the React single-page app
```

## 📝 Notes

- Video pitch URLs in the seed data are placeholders; configure real file storage for production.
- Email scoring uses simple rules and could later be improved with NLP or AI-based feedback.

## 👤 Author

**Massouane Abdelati** · [GitHub](https://github.com/amassouane)
