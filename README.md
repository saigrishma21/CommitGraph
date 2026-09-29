# 🚀 CommitGraph

### AI-Powered Persistent Meeting Memory & Commitment Tracking System

CommitGraph is an AI-powered meeting assistant designed to transform unstructured meeting notes into **structured, persistent, and searchable commitment memory**.

During meetings, important commitments, deadlines, responsibilities, and follow-up actions can easily be forgotten. CommitGraph addresses this problem by using **AI agents and persistent memory** to identify commitments from meeting notes, store them, track their status, recall historical information, and help users prepare for future meetings.

---

## 🎯 Problem Statement

Important commitments made during meetings are often lost because:

* Meeting discussions contain large amounts of unstructured information.
* Action items may not be recorded properly.
* Previous meeting information is difficult to search.
* Team members may forget who committed to what.
* Deadlines and commitment statuses can become unclear.
* Preparing for follow-up meetings requires manually reviewing old notes.

CommitGraph converts meeting discussions into persistent knowledge that can be retrieved whenever required.

---

## 💡 Our Solution

CommitGraph creates a continuous memory of meetings.

Instead of treating every meeting as an independent event, the system:

1. Accepts meeting notes from the user.
2. Uses an AI agent to identify actual commitments.
3. Extracts important details such as person, commitment, deadline, status, and context.
4. Stores structured commitment information in SQLite.
5. Stores relevant information in persistent memory using Hindsight.
6. Allows users to ask questions about previous meetings.
7. Retrieves relevant memories to generate contextual answers.
8. Helps users prepare for future meetings.

### Core Workflow

```text
                 ┌─────────────────────┐
                 │     Meeting Notes   │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │     AI Agent        │
                 │ Commitment Extractor│
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │    SQLite Database  │
                 │ Meetings & Tasks    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Hindsight Memory    │
                 │ Persistent Context  │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Memory Recall / AI  │
                 │ Question Answering  │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ User / Future       │
                 │ Meeting Preparation  │
                 └─────────────────────┘
```

---

# ✨ Key Features

## 🤖 AI Commitment Extraction

CommitGraph analyzes natural-language meeting notes and identifies concrete commitments.

The system extracts information such as:

* Person responsible
* Commitment
* Deadline
* Status
* Context

The AI is instructed to avoid inventing information that is not present in the meeting notes.

---

## 🧠 Persistent Meeting Memory

CommitGraph integrates with **Hindsight** to retain meeting-related information beyond a single session.

This allows the system to remember:

* Previous commitments
* Meeting context
* Deadlines
* Status information
* Dependencies
* Follow-up information

---

## 🔎 Intelligent Memory Recall

Users can ask questions about previous meetings.

For example:

```text
What did Rahul commit to in the previous meeting?
```

or:

```text
What pending commitments are related to the API integration?
```

The system retrieves relevant memories and uses the AI agent to generate a contextual response.

---

## 📅 Future Meeting Preparation

Users can prepare for a meeting with a specific person.

The system retrieves relevant historical information and can provide:

* Previous commitments
* Pending work
* Recorded completion information
* Deadlines
* Dependencies
* Blockers
* Follow-up points

This reduces the need to manually search through previous meeting notes.

---

## 📊 Commitment Tracking

Commitments are stored in a structured database and can be tracked using statuses such as:

```text
PENDING
IN_PROGRESS
COMPLETED
```

The system maintains the distinction between recorded facts and assumptions. For example, an expired deadline does not automatically mean that a commitment was completed.

---

# 🏗️ System Architecture

CommitGraph follows a frontend-backend architecture.

```text
┌──────────────────────────────┐
│        React Frontend        │
│                              │
│ • Meeting Input              │
│ • Commitments                │
│ • Questions                  │
│ • Meeting Preparation        │
└───────────────┬──────────────┘
                │
                │ REST API
                ▼
┌──────────────────────────────┐
│       FastAPI Backend        │
│                              │
│ • API Endpoints              │
│ • Business Logic             │
│ • Validation                 │
└───────┬───────────┬──────────┘
        │           │
        ▼           ▼
┌────────────┐  ┌────────────────┐
│   SQLite   │  │   AI Agent     │
│  Database  │  │     Groq       │
└────────────┘  └───────┬────────┘
                        │
                        ▼
                ┌────────────────┐
                │    Hindsight   │
                │ Persistent     │
                │ Memory         │
                └────────────────┘
```

---

# 🛠️ Technology Stack

## Frontend

* React
* JavaScript
* Vite
* HTML
* CSS
* Fetch API

## Backend

* Python
* FastAPI
* Pydantic
* REST APIs

## Database

* SQLite

## Artificial Intelligence

* Groq
* AI Agents
* Structured information extraction
* Retrieval-based question answering

## Persistent Memory

* Hindsight

## Development Tools

* Git
* GitHub
* VS Code
* Python Virtual Environment
* npm

---

# 📁 Project Structure

```text
CommitGraph/
│
├── backend/
│   │
│   ├── main.py
│   ├── agent.py
│   ├── database.py
│   ├── models.py
│   ├── hindsight_memory.py
│   ├── requirements.txt
│   ├── reset_hindsight.py
│   └── ...
│
├── frontend/
│   │
│   ├── src/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── ...
│   │
│   ├── public/
│   ├── package.json
│   ├── vite.config.js
│   └── ...
│
├── .gitignore
├── README.md
└── ...
```

---

# 🔧 Backend Components

### `main.py`

The main FastAPI application.

It is responsible for:

* Creating the FastAPI application
* Configuring CORS
* Initializing the database
* Defining API endpoints
* Processing meetings
* Retrieving commitments
* Handling questions
* Preparing meetings
* Updating commitment status

---

### `agent.py`

Contains AI-agent functionality.

It is responsible for:

* Processing meeting notes
* Extracting commitments
* Generating structured information
* Answering questions using retrieved context
* Preparing meeting summaries

---

### `database.py`

Handles SQLite database operations.

It manages information related to:

* Meetings
* Commitments
* Status
* Deadlines
* Context

---

### `models.py`

Contains Pydantic data models.

These models provide:

* Request validation
* Response structure
* Type checking
* Consistent API data formats

---

### `hindsight_memory.py`

Handles integration with the Hindsight persistent-memory system.

It is responsible for:

* Initializing the Hindsight client
* Storing memories
* Recalling relevant memories
* Managing persistent context

---

### `reset_hindsight.py`

Utility script used when the stored Hindsight memory needs to be reset or cleared for a fresh project state.

---

# 🌐 Frontend Components

The React frontend provides the user interface for interacting with CommitGraph.

The application allows users to:

* Enter meeting details
* Process meetings
* View commitments
* Ask questions
* Prepare for meetings
* View memory-related activity

React state management is used to handle:

* Form inputs
* API responses
* Loading states
* Commitment information
* Questions and answers

---

# 🔗 API Endpoints

The FastAPI backend exposes endpoints for the main application operations.

| Endpoint                    | Purpose                                           |
| --------------------------- | ------------------------------------------------- |
| `/process-meeting`          | Processes meeting notes and extracts commitments  |
| `/commitments`              | Retrieves stored commitments                      |
| `/prepare-meeting/{person}` | Prepares information for a meeting with a person  |
| Question/Memory endpoint    | Retrieves relevant memories and answers questions |
| Status update endpoint      | Updates commitment status                         |

The exact API paths may vary depending on the current implementation in the repository.

---

# ⚙️ Installation and Setup

## Prerequisites

Install the following before running the project:

* Python 3.10+
* Node.js
* npm
* Git

You also need the required AI and persistent-memory service credentials.

---

# 🚀 Backend Setup

Open a terminal and navigate to the backend directory:

```bash
cd backend
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment on Windows:

```bash
venv\Scripts\activate
```

On Linux/macOS:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# 🔐 Environment Variables

Create a `.env` file inside the backend directory.

Example:

```env
GROQ_API_KEY=your_groq_api_key
HINDSIGHT_BASE_URL=your_hindsight_url
HINDSIGHT_API_KEY=your_hindsight_api_key
HINDSIGHT_BANK_ID=your_bank_id
```

### ⚠️ Security

Never commit your `.env` file to GitHub.

Add it to `.gitignore`:

```text
.env
```

Replace the example values with your own credentials.

---

# ▶️ Run the Backend

From the backend directory:

```bash
uvicorn main:app --reload
```

The backend will normally be available at:

```text
http://127.0.0.1:8000
```

FastAPI's interactive API documentation can be accessed at:

```text
http://127.0.0.1:8000/docs
```

---

# ▶️ Run the Frontend

Open another terminal.

Navigate to the frontend:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Start the Vite development server:

```bash
npm run dev
```

Vite will display the local development URL in the terminal, normally similar to:

```text
http://localhost:5173
```

Open that URL in your browser.

---

# 🔄 How a Meeting Is Processed

### Step 1 — User enters meeting information

The user provides:

```text
Meeting Title
Meeting Notes
```

### Step 2 — Frontend sends the request

React sends the meeting information to the FastAPI backend.

### Step 3 — Backend stores the meeting

The meeting information is stored in SQLite.

### Step 4 — AI analyzes the notes

The AI agent identifies actual commitments.

For example:

```text
Rahul will complete the authentication API by Friday.
```

The system can extract:

```text
Person: Rahul
Commitment: Complete the authentication API
Deadline: Friday
Status: PENDING
```

### Step 5 — Commitment is stored

The structured commitment is saved in the database.

### Step 6 — Memory is created

Relevant information is stored in Hindsight for persistent recall.

### Step 7 — Future retrieval

When a user asks about the commitment, relevant memories are retrieved.

### Step 8 — AI generates the response

The AI uses the retrieved context to provide an answer.

---

# 🧠 Example Use Case

Consider a software development team meeting.

Meeting notes:

```text
Rahul will complete the login API by Friday.

Priya will test the API after Rahul finishes it.

The team will review the authentication module next Monday.
```

CommitGraph can identify:

```text
Rahul
→ Complete login API
→ Friday
→ PENDING

Priya
→ Test login API
→ After Rahul completes it
→ PENDING
```

Later, a user can ask:

```text
What did Rahul commit to?
```

The system retrieves the stored information and provides the relevant answer.

The user can also ask:

```text
What should I follow up with Rahul about?
```

The persistent memory allows the system to connect the current question with previous meeting information.

---

# 🔒 Security Considerations

The project follows several basic security practices:

* API keys are stored in environment variables.
* `.env` is excluded from Git.
* Input data is validated using Pydantic.
* CORS is configured for frontend-backend communication.
* Sensitive credentials should never be committed to the repository.

For production deployment, additional authentication, authorization, secret management, HTTPS and database security should be implemented.

---

# 🧪 Testing

The application can be tested by:

1. Starting the backend.
2. Starting the frontend.
3. Creating a sample meeting.
4. Adding clear commitments.
5. Processing the meeting.
6. Checking the extracted commitments.
7. Asking questions about previous meetings.
8. Testing meeting preparation.
9. Updating commitment status.
10. Verifying persistent-memory retrieval.

---

# 📌 Future Enhancements

Possible future improvements include:

* User authentication
* Team-based access control
* PostgreSQL integration
* Cloud deployment
* Email notifications
* Deadline reminders
* Calendar integration
* Slack/Teams integration
* Advanced analytics dashboard
* Commitment history visualization
* Multi-user collaboration
* Voice-to-text meeting input
* Automatic meeting transcription
* Mobile application
* Role-based permissions

---

# 🏆 HackWithHyderabad

CommitGraph was developed as part of the **HackWithHyderabad Hackathon**.

The project focuses on:

* AI Agent Design
* Persistent Memory
* Real-World Problem Solving
* AI-powered Productivity
* Meeting Intelligence

The project gave us hands-on experience in designing an end-to-end AI application that combines a modern frontend, REST backend, database persistence, AI processing and long-term memory.

---

# 👥 Team

**Team Name:** `[Add Your Team Name]`

**Team Members:**

* `[Member 1]`
* `[Member 2]`
* `[Member 3]`
* `[Member 4]`

---

# 🎥 Demo

**Project Demo Video:**
`[Add your video link]`

---

# 📄 Article

**Project Article:**
`[Add your article link]`

---

# 🔗 Project Repository

**GitHub:**
`[Add your GitHub repository URL]`

---

# 📱 Social Links

**LinkedIn:**
`[Add LinkedIn post URL]`

**Reddit:**
`[Add Reddit post URL]`

---

# 📜 License

This project is developed for educational and hackathon purposes.

---

## ⭐ Acknowledgements

Thanks to the **HackWithHyderabad** organizers for providing the opportunity to explore AI agents, persistent memory and real-world problem solving through this hackathon.

---

### Built with ❤️ using AI, persistent memory and modern web technologies.
