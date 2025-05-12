## Phase 4 – Project Presentation

### 🎯 Project Title
**Optidev.fi – Interactive Programming Platform with Quizzes, Code Editor & Linux Environment**

### 📝 Project Overview
Optidev.fi is an educational platform designed for students learning programming and Linux basics. It offers interactive quizzes, a browser-based code editor, and a terminal connected to pre-configured Docker containers. The project targets high school and early university students, helping them practice real-world skills in a guided, secure environment.

### 📌 Use Case Summary
Refer to Phase 1 for original definitions.

| Use Case                                      | Implemented | Demonstration / Notes                                     |
|----------------------------------------------|-------------|-----------------------------------------------------------|
| Student takes a quiz                         | Yes         | Multiple-choice quiz with score tracking.  |
| Student launches learning environment        | Yes         | Docker container via Proxmox & Cloudflare Tunnel. |
| Admin adds new module                        | Yes         | Admin dashboard for managing modules.     |
| Admin adds new question to existing quiz     | Yes         | Implemented in Phase 3.                      |
| Student views personal profile and progress  | Yes (Secured in Phase 3) | Session-based view only.              |

### ✍️ Technical Implementation
- **Frontend:** Next.js with Tailwind CSS, responsive design.  
- **Backend:** Next.js API routes (Node.js), REST API.  
- **Authentication:** Google/GitHub OAuth via `next-auth`, JWT sessions.  
- **Database:** MongoDB for users, quizzes, modules, and stats.  
- **Code Editor:** Monaco Editor with OpenAI integration for suggestions.  
- **Docker Integration:** Terminal access via local Proxmox VM & Cloudflare Tunnel.

Key implementations include:
- Authenticated profile routing with secure session.  
- Modular admin content management tools.  
- Docker orchestration tied to user actions.

### 🚂 Development Process
- **Phase 1:** Defined core use cases, UI mockups, and backend structure.  
- **Phase 2:** Built core features (quizzes, login, container launch, admin panel).  
- **Phase 3:** Added quiz question editing and fixed profile access security.

Key decisions:
- Used Cloudflare Tunnel for secure container access.  
- Chose MongoDB for flexibility in quiz and user data.  
- Adopted session-based routing for privacy.

### 📦 Implementation of phase 3
- **Quiz Management:** Admin can add/edit questions and modules.
- **User Profiles:** Profile access secured wiht session handeling only, not by url.
- example: `/profile?uid=123` is not accessible, only `/profile` is.
- example code:
```tsx
import React from 'react'
import Profile from '@/components/Profile/Profile'
import prisma from '@/lib/prisma/prisma'
import { Session, getServerSession } from 'next-auth'
import { authOptions } from "@/lib/utils/backend/authOptions"

export default async function ProfilePage() {
    const session:Session | null = await getServerSession(authOptions) as Session
    const data = await prisma.userScores.findMany({where: {userId: session?.user.id }})
    const score = await prisma.code.findMany({where: { cleared: { hasEvery: [session?.user.email],}},include: {course: true}})
    return (
    <Profile results={data} code={score} />
  )
}
```

### ☀️ Reflection and Future Work
**What went well:**  
- Docker container integration was stable.  
- UI was intuitive based on initial testing.  
- OAuth login and session tracking worked reliably.

**Challenges:**  
- Secure container access was technically demanding.  
- Real-time collaborative features were out of scope.

**Future work:**  
- Add peer review or collaborative coding features.  
- Migrate to PostgreSQL for relational advantages.  


### 📊 Work Hours Log

| Date     | Used hours | Subject(s)             | Outcome                          |
| :------- | :--------: | :--------------------: | :------------------------------: |
|1.3.2023-15.4.2025|    At least 150      | Planning and work hour overall  | Created optidev.fi           |
| 7.4.2025 |     2      | Planning the phase 1   | Defined User Personas            |
| 8.4.2025 |     2      | Planning the phase 1   | Defined Use Cases and User Flows |
| 15.4.2025 |     2      | Planning the phase 2   | Documented optidev.fi           |                           |



