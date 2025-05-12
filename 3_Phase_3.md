## Phase 3 – Extra Feature or Improvements (Optional)

### 🎯 Chosen Use Case or Feature to Improve
This phase focuses on two key areas:

1. Expanding the admin console to allow adding new questions to existing quizzes.  
2. Fixing a security vulnerability that allowed users to access other users' profiles via URL manipulation.

These were selected because the admin tool was incomplete without the ability to modify quizzes, and securing user profile data is a critical privacy requirement.

### 🔍 Original Definition
Referenced from Phase 1 Use Cases:

- *"Admin Adds New Module"*: included quiz creation and also editing existing questions, but not enable to add new question to already created quiz.  
- *"Student Takes a Quiz"* and *"Student Profile"*: implied access to private quiz results and user data.

### 🔄 Implementation

#### Admin Console Improvement: Add New Question to Quiz

**Technical Changes:**

- UI: New form in the admin dashboard to input question, answer choices, and correct answer.
- Quiz selection dropdown or searchable list.
- Append questions to an existing quiz without full recreation.

**Technologies Used:**

- Next.js (frontend)  
- MongoDB (quiz document update)  
- REST API (`POST /api/quiz/:id/add-question`)

**Challenges & Solutions:**

- Validating quiz IDs and ensuring data integrity in updates – resolved via schema checks and server-side validation.  
- Keeping the UI intuitive for multi-question input – solved with component modularity and real-time feedback.

#### Security Fix: Restrict Profile Access

**Technical Changes:**

- Removed `?id=` query usage in `/profile` route.
- Used `getServerSession` from `next-auth` to securely identify the user.
- Refactored server-side logic to reject unauthorized access.

**Technologies Used:**

- Next.js server-side rendering (SSR)  
- `next-auth` for secure session handling

**Challenges & Solutions:**

- Handling unauthenticated sessions without breaking UX – resolved with redirect or safe fallback message.  
- Validating all routes for similar issues – started an audit
