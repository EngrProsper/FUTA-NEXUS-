FUTA NEXUS — CBT Practice Hub
Free, offline-ready CBT practice app for 100-level students at the Federal University of Technology, Akure (FUTA).
Overview
FUTA NEXUS is a single-file web application that helps 100-level FUTA students prepare for their Computer-Based Tests (CBT). It provides a structured question bank across all major 100-level courses, with instant feedback, topic mastery tracking, and a study streak system — all without requiring an internet connection after the initial load.
The question bank is hosted on GitHub Gist and fetched dynamically on every app load. Updating the question bank requires no app redeployment — only a Gist update.
Live App
Open FUTA NEXUS
Features
598 questions across 6 active courses with full explanations
4 practice modes — FUTA Survival (25Q, 12 min), Mastery Mode (40Q, 25 min), Sprint (15Q, 8 min), and Study Mode (unlimited, no timer)
Cloud question bank — questions load from GitHub Gist; updates go live instantly for all users
Topic mastery tracking — per-course, per-topic performance scores updated after every test
Study streak — tracks consecutive days of practice
Answer review — full review of every test with correct answers and explanations
Performance chart — bar chart of your last 10 test scores
Exam timetable — live countdown to each exam with direct Practice shortcuts
Ask the Tutor — keyword-based tutor covering PHY101, MTS101, GNS103 and more
Light and dark mode — GitHub-inspired design system
Haptic feedback — native vibration on option selection, correct/wrong answers, and navigation
Fully offline after load — works without internet once the question bank is cached
Zero dependencies — vanilla HTML, CSS, and JavaScript; no frameworks, no build step
Course Coverage
Course
Questions
Topics
MTS 101
135
Set Theory, Sequences & Series, Polynomials, Trigonometry, Binomial Theorem
GNS 103
191
Library Types, Reference Sources, OPAC, DDC/LC Classification, Cataloguing, Internet & Search Strategy
GNS 101
60
Parts of Speech, Grammar (Phrases, Clauses, Sentences), Time Management
CHE 101
91
Chemical Kinetics, Atomic Theory, Quantum Numbers, Electronic Configuration, Radioactivity
GET 101
65
History of Engineering, Industrial Revolutions, Nigerian Engineering Bodies, Ages of Man, Ancient Materials
PHY 103
56
Past questions across core physics topics
Total
598

Architecture
FUTA-CBT-APP/
└── index.html          # Complete app — single file, no build required
Question Bank (GitHub Gist)
└── futa_cbt_questions.json
    ├── courses
    │   ├── MTS101 { name, full, questions: [...] }
    │   ├── GNS103 { ... }
    │   ├── CHE101 { ... }
    │   └── ...
    └── lastUpdated
The app fetches the Gist JSON on every load with cache-busting (?t=Date.now()). Any course added to the JSON automatically becomes active in the app — no code changes required. Any course absent from the JSON automatically appears as "Coming Soon".
All user data (test history, mastery scores, streak, profile) is stored in localStorage using the fnx_ prefix.
Question Bank JSON Structure
Each question follows this schema:
{
  "id": 1,
  "block": "Topic Name",
  "q": "Question text",
  "opts": ["Option A", "Option B", "Option C", "Option D"],
  "ans": "Option A",
  "expl": "Explanation of the correct answer.",
  "source": "past_question",
  "verified": true,
  "flagged": false
}
Updating the Question Bank
Edit futa_cbt_questions.json on GitHub Gist
Click Update public gist
All users receive the updated questions on their next app load
No redeployment of the app is needed.
Deployment
The app is deployed via GitHub Pages from the main branch. Any commit to index.html goes live automatically within seconds.
To run locally, simply open index.html in any browser. Note that the question bank fetch will fail locally due to browser CORS restrictions on file:// URLs — this is expected behaviour. Deploy to any static hosting service for full functionality.
Roadmap
[ ] Add CSC 101 and BIO 101 question banks
[ ] Expand PHY 103 with categorised topics
[ ] Add shareable result cards
[ ] Add per-question difficulty rating
[ ] Progressive Web App (PWA) support for home screen installation
Built By
Omoreme Prosper Ogheneochuko
Building solutions for the future.
License
MIT License — free to use, share, and adapt with attribution.
