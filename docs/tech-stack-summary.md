# FitFlow Proposed Technology Stack

| Layer | Selection | Purpose |
|---|---|---|
| Android and iOS | React Native | Shared mobile interface |
| Browser screens | React Native Web | Shared components where suitable |
| Main API | Node.js with Express | Business rules, permissions, REST endpoints |
| Structured records | PostgreSQL | Profiles, workouts, nutrition |
| Identity | Firebase Authentication | Sign-in and identity tokens |
| Community real time | Cloud Firestore | Private circles and live social updates |
| AI service | Python FastAPI | Optional cloud model inference |
| On-device AI | LiteRT | Optional local model inference |
| Cache | Redis | Short-lived non-sensitive data |

The backend verifies Firebase tokens and enforces authorization for PostgreSQL records. Firestore rules restrict access to private social circles. Health data stays out of public posts and shared caches.
