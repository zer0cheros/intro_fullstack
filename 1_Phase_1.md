## Project Overview

This project is already started and I’ve created some notes for myself before I started this project. I’ve started to create a simple site for quizzes and exercises for students. The site is a simple quiz site where students can take quizzes and exercises to learn programming languages.

Then after the site expanded, I added a Docker container with a pre-configured environment for students to learn the Linux environment. The site also has a code editor for solving code challenges.

https://optidev.fi

# Project Phase 1 - Definition and Planning

- Student logs in and selects a programming language to learn
- Student launches a Docker container with a pre-configured environment
- Student completes a coding exercise using the integrated code editor
- Student takes a quiz to test understanding of the current topic
- Admin uploads or manages course modules and exercises

## 1. User Personas

**Alex, 16** – High school student new to coding, needs step-by-step guidance.  
**Ravi, 18** – Student looking to practice specific topics.  
**Emma, 17** – Student who wants to learn Linux skills.

## 2. Use Cases and User Flows

### Use Case 1: Student Takes a Quiz

1. Student logs in  
2. Selects a quiz topic from the dashboard  
3. Answers multiple-choice and code-based questions  
4. Submits the quiz and receives immediate feedback  
5. Quiz score is stored in the user profile  

### Use Case 2: Student Launches Learning Environment

1. Student selects a module (e.g., "Intro to Linux")  
2. Clicks “Launch Docker container”  
3. A Docker container spins up in the background  
4. Student gains terminal access and answers questions  

### Use Case 3: Admin Adds New Module

1. Admin accesses the `/admin` page  
2. Clicks “Create Module”  
3. Adds metadata (title, description, difficulty)  
4. Uploads quizzes and exercises for the Docker image  
5. Module goes live to students  

## 3. UI Prototypes

- `/profile` – Stats view: Lists modules, quiz progress, and scores  
- `/quiz` – Quiz view: Multiple-choice interface with score feedback  
- `/code` – Code editor view: Full-width editor pane with run button and console output  
- `/admin` – Admin panel: Table of modules with edit/add/delete buttons  

## 4. Information Architecture and Technical Design

### Frontend

- Built with Next.js (using Tailwind CSS)  
- Pages: Home, Profile, Quiz, Code Editor, Docker Module, Admin  

### Backend

- Node.js (built-in API routes in Next.js)  
- `/api` – REST API for quizzes and progress tracking  

### Containers

- Docker containers running on local Proxmox VMs  
- Virtual networking for isolation  
- Prebuilt images for web-based terminal use (using Whetty)  
- Zero-trust web terminal access via Cloudflare Tunnel  

### Storage

- MongoDB (PostgreSQL might be used in future)  
- Stores exercises, quiz content, user data, and stats  

### Security

- Using `next-auth` for authentication/authorization  
- JWT for session management  
- Cloudflare for traffic management  
- Google and GitHub OAuth login  
- Middleware for auth checks and role-based access (admin vs student)  

## 5. Project Management and User Testing

- Time log: maintained in `/timelog.md`

### Testing Plan

- After Phase 2, test with 2–3 real students  
- Focus on usability, onboarding, and identifying bugs  
- Use feedback to improve UI/UX before Phase 3  
