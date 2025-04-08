## Project Overview
    This project is allready started and i´ve created som notes for myself before i strated this project. I´ve strated to create a simple site for quizzes and exercises for students. The site is a simple quiz site where students can take quizzes and exercises to learn programming languages. Then after the site expanded, I´ve added a Docker container with a pre-configured environment for students to learn linux-enviroment. The site also have a code editor for solving code challenges. 

https://optidev.fi


# Project phase 1 - Definition and planning
	 
- Student logs in and selects a programming language to learn

- Student launches a Docker container with a pre-configured environment

- Student completes a coding exercise using the integrated code editor

- Student takes a quiz to test understanding of the current topic

- Admin uploads or manages course modules and exercises

## 1. User Personas

Alex, 16 – High school student new to coding, needs step-by-step guidance.

Ravi, 18 – Student looking to practice specific topics.

Emma, 17 – Student and want to learn Linux skills.

## 2. Use Cases and User Flows

- Use Case 1: Student Takes a Quiz Flow:

    1. Student logs in

    2. Selects a quiz topic from the dashboard

    3. Answers multiple-choice and code-based questions

    4. Submits the quiz and receives immediate feedback

    5. Quiz score is stored in the user profile


- Use Case 2: Student Launches Learning Environment Flow:

    1. Student selects a module (e.g., course name”)

    2. Clicks “Launch Docker container”

    3. A Docker container spins up in the background 

    4. Student gains terminal and answers questions

- Use Case 3: Admin Adds New Module Flow:

    1. When admin you can access /admin page

    2. Clicks “Create Module”

    3. Adds metadata (title, description, difficulty)

    4. Uploads quizzes, exercises for Docker image

    5. Module goes live to students

## 3. UI Prototypes
- /profile - Stats view: Lists modules, quiz progress, and scores.

- /quiz - Quiz View: Multiple-choice interface with score feedback.

- /code - Code Editor View: Full-width editor pane with run button and console output. 

- /admin - Admin Panel: Table of modules, with edit/add/delete buttons.

## 4. Information Architecture and Technical Design

### Frontend:

- Built with NextJs (using Tailwind CSS)
- Pages: Home, Profile, Quiz, Code Editor, Docker Module, Admin

### Backend:

- Node.js built in NextJs
- /api - REST API for quizzes, and progress tracking

### Containers:

- Docker containers running on local proxmox virtual machines
- Virtual networking for all Docker containers for isolation
- Prebuilt images form webbased terminal use (whetty)
- Zero-thrust for web-based terminal access through Cloudflare tunnel

### Storage:

- Database: MongoDB but behaps i will use PostgreSQL in future
- File storage for exercises, quiz content, users and stats

### Security:

- Here I´m using next-auth for authentication and authorization
- JWT for session management
- Traffic management with Cloudflare
- Authentication via JWT or OAuth (Google, GitHub)
- Middleware for all API routes to check authentication
- Middleware for role-based access control (admin vs. student)

## 5. Project Management and User Testing

- Time Log: Maintained in /timelog.md


### Testing Plan:

- After Phase 2, test with 2–3 real students

- Focus on usability, onboarding, and identifying bugs

- Use feedback to adjust UI/UX before Phase 3