# Skill Gap Analyzer - AI-Powered Career Readiness Platform

A modern, full-stack web application that analyzes your skills, identifies gaps, and provides personalized learning roadmaps powered by artificial intelligence.

## 🚀 Features

### Core Features
- **Resume Upload & Analysis**: Upload PDF resumes and AI extracts skills, experience, education, and projects
- **Skill Gap Detection**: Identify missing, weak, and matching skills for target roles
- **Readiness Score**: Get a percentage-based readiness assessment for your target position
- **AI-Powered Insights**: Receive personalized career advice and improvement suggestions
- **Learning Roadmap**: Get a customized learning plan with estimated timelines and resources
- **Progress Tracking**: Monitor your skill development journey
- **Interactive Dashboard**: Beautiful UI with charts and analytics

### Technical Features
- **Modern Design**: Glassmorphism effects, gradient backgrounds, smooth animations
- **Fully Responsive**: Works seamlessly on desktop, tablet, and mobile
- **Dark/Light Mode**: Support for both themes
- **User Authentication**: Secure NextAuth integration with credentials provider
- **Database**: PostgreSQL with Prisma ORM
- **AI Integration**: OpenAI API for intelligent analysis
- **Charts & Analytics**: Recharts for data visualization
- **PDF Export**: Generate and download analysis reports

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 15 with TypeScript
- **Styling**: Tailwind CSS with custom components
- **UI Components**: shadcn/ui inspired custom components
- **Animations**: Framer Motion for smooth interactions
- **State Management**: Zustand (ready to integrate)
- **Charts**: Recharts for data visualization

### Backend
- **Runtime**: Node.js
- **API**: Next.js API Routes
- **Database**: PostgreSQL
- **ORM**: Prisma
- **Authentication**: NextAuth with credentials provider
- **AI**: OpenAI API
- **File Handling**: Node.js fs/streams

### DevOps & Deployment
- **Deployment**: Vercel-ready configuration
- **Database**: PostgreSQL
- **Environment Management**: .env configuration
- **Package Manager**: npm

## 📋 Prerequisites

- Node.js >= 18.17.0
- PostgreSQL database
- OpenAI API key
- npm or yarn

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone <repository-url>
cd skill-gap-analyzer
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Set Up Environment Variables
```bash
cp .env.example .env.local
```

Edit `.env.local` with your configuration:
```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/skill_gap_analyzer"

# NextAuth
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your-secret-key-min-32-chars-long"

# OpenAI
OPENAI_API_KEY="sk-your-openai-api-key"

# Other
NEXT_PUBLIC_APP_URL="http://localhost:3000"
```

### 4. Set Up Database
```bash
# Push schema to database
npm run db:push

# Run seed script (optional, creates demo user)
npm run db:seed
```

Demo user:
- Email: `demo@skillgap.ai`
- Password: `demo@123`

### 5. Start Development Server
```bash
npm run dev
```

Visit http://localhost:3000

## 📚 Usage

### For Users
1. **Sign Up or Login**: Create an account or use demo credentials
2. **Upload Resume**: Go to Dashboard > Upload Resume
3. **Select Target Role**: Choose your desired job role
4. **View Analysis**: See your readiness score and skill breakdown
5. **Generate Roadmap**: Get a personalized learning plan
6. **Track Progress**: Monitor your improvement over time

### For Developers

#### Project Structure
```
.
├── src/
│   ├── app/                    # Next.js App Router
│   │   ├── api/               # API routes
│   │   ├── dashboard/         # Protected dashboard routes
│   │   ├── auth/              # Authentication pages
│   │   └── page.tsx           # Landing page
│   ├── components/            # React components
│   │   ├── auth/              # Auth components
│   │   ├── dashboard/         # Dashboard components
│   │   ├── analysis/          # Analysis components
│   │   ├── roadmap/           # Roadmap components
│   │   ├── landing/           # Landing page components
│   │   └── ui/                # Reusable UI components
│   ├── lib/                   # Utilities and helpers
│   │   ├── auth.ts            # NextAuth configuration
│   │   └── prisma.ts          # Prisma client
│   ├── services/              # Business logic
│   │   └── aiService.ts       # OpenAI integration
│   ├── types/                 # TypeScript types
│   ├── utils/                 # Utility functions
│   └── styles/                # Global styles
├── prisma/
│   ├── schema.prisma          # Database schema
│   └── seed.js                # Seed script
├── public/                    # Static assets
├── .env.example               # Example environment variables
└── package.json               # Dependencies
```

#### Key Files

**Database Schema**: [prisma/schema.prisma](prisma/schema.prisma)
- Users, Resumes, SkillAnalyses, LearningPlans, SavedReports

**API Routes**:
- `POST /api/auth/register` - User registration
- `POST /api/resume/upload` - Resume upload and analysis
- `POST /api/roadmap/generate` - Generate learning roadmap
- `PUT /api/settings` - Update user settings
- `GET /api/user` - Get current user

**Components**:
- `ResumeUploader` - Resume file upload interface
- `AnalysisResults` - Display skill analysis results
- `RoadmapTimeline` - Learning roadmap timeline
- `DashboardOverview` - Charts and analytics

## 🔧 Configuration

### Database

Create a PostgreSQL database:
```bash
createdb skill_gap_analyzer
```

Update `DATABASE_URL` in `.env.local`:
```
DATABASE_URL="postgresql://username:password@localhost:5432/skill_gap_analyzer"
```

### OpenAI API

1. Get your API key from https://platform.openai.com/api-keys
2. Add to `.env.local`:
```
OPENAI_API_KEY="sk-your-key-here"
```

### NextAuth

Generate a secret:
```bash
openssl rand -base64 32
```

Add to `.env.local`:
```
NEXTAUTH_SECRET="your-generated-secret"
```

## 🚀 Deployment

### Deploy to Vercel

1. Push your code to GitHub
2. Connect repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

```bash
vercel
```

### Environment Variables on Vercel
- `DATABASE_URL`
- `NEXTAUTH_URL` (https://your-domain.com)
- `NEXTAUTH_SECRET`
- `OPENAI_API_KEY`

## 📊 Database Schema

### Users
- id, name, email, password, role, createdAt, updatedAt
- Relations: resumes, analyses, learningPlans, savedReports

### Resumes
- id, userId, fileName, extractedText, skills, experience, education, projects, certifications
- Relations: user, analyses

### SkillAnalyses
- id, userId, resumeId, targetRole
- matchedSkills, missingSkills, weakSkills, readinessScore
- aiInsights, strengthSummary, improvementAreas
- Relations: user, resume, learningPlan

### LearningPlans
- id, userId, analysisId
- roadmapItems, estimatedDays, priorityOrder
- completedItems, progressPercentage
- recommendations, studyPlan

### SavedReports
- id, userId, title, description
- reportData, pdfPath

## 🎯 Role Requirements

The system includes industry-standard requirements for:
- Frontend Developer
- Backend Developer
- Data Scientist
- DevOps Engineer
- Product Manager
- Full Stack Developer
- UX/UI Designer
- Mobile Developer

Easily add more roles in `src/utils/roleRequirements.ts`

## 🤖 AI Features

The application uses OpenAI to:
1. **Analyze Skills**: Extract and understand skills from resume text
2. **Compare Requirements**: Match skills against role requirements
3. **Generate Insights**: Provide career advice and recommendations
4. **Create Roadmaps**: Design personalized learning plans
5. **Suggest Improvements**: Recommend resume enhancements
6. **Prepare Interviews**: Generate interview questions

## 🔐 Security

- Passwords hashed with bcrypt
- NextAuth for secure sessions
- CSRF protection
- Environment variables for sensitive data
- API routes protected with authentication
- Prisma for SQL injection prevention

## 📦 Scripts

```bash
# Development
npm run dev              # Start dev server
npm run build            # Build for production
npm run start            # Start production server
npm run lint             # Run ESLint

# Database
npm run db:push          # Push schema changes
npm run db:seed          # Run seed script
npm run db:studio        # Open Prisma Studio
npm run db:generate      # Generate Prisma client

# Utilities
npm run type-check       # Check TypeScript
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Built with modern web technologies
- AI powered by OpenAI
- Charts by Recharts
- UI inspired by Vercel and leading SaaS platforms
- Icons by Lucide React



## 🗺️ Future Roadmap

- [ ] Video tutorials for learning resources
- [ ] Community skill matching
- [ ] Job board integration
- [ ] Real-time collaboration
- [ ] Mobile app (React Native)
- [ ] Advanced analytics
- [ ] Custom role creation
- [ ] Team/company features
- [ ] Certification tracking
- [ ] Mentor matching

---

**Built with ❤️ for career advancement**
