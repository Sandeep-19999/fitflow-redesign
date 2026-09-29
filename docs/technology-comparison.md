# FitFlow Technology Comparison

IT3060 HCI Lab Exercise 05, Activities 1 and 2. These are qualitative assessments for the case study, not measured benchmarks.

## Frontend options

| Criterion | Flutter | React Native | Kotlin Multiplatform | Swift and SwiftUI |
|---|---|---|---|---|
| Development speed | Fast with a shared Dart UI | Fast with React skills | Moderate, depending on shared UI approach | Fast for iOS; Android is separate |
| Code reuse | High across mobile and web | High on mobile; browser via React Native Web | Shared logic, with platform UI work | Apple platforms only |
| Performance | Strong compiled UI | Strong for standard app flows | Native UI performance | Native Apple UI |
| Ecosystem | Large package ecosystem | Large React and RN ecosystem | Growing libraries | Mature Apple ecosystem |
| Learning curve | Learn Dart and widgets | Learn React and native tooling | Learn Kotlin and platform UIs | Learn Swift and Android separately |
| Web | Directly supported | React Native Web, with package checks | Additional UI work | No direct browser UI |
| AI and ML | Native plugins or APIs | Native modules or APIs | Native SDKs on each platform | Apple native frameworks |
| Real time | Firebase or sockets | Firebase or WebSockets | Platform SDK integration | Apple platform SDKs |
| Maintenance | One principal UI codebase | Shared mobile UI, test web separately | More than one target UI | Separate Android implementation |
| Security | Depends on implementation | Depends on implementation | Depends on implementation | Depends on implementation |

**Recommendation:** React Native for Android and iOS, with React Native Web for suitable browser screens. It aligns with the FitFlow case study and offers a shared mobile implementation. Test camera, accessibility, ML modules and web-specific behavior. Flutter is a strong alternative when a single consistent rendered UI has priority.

## Backend options

| Option | Strength for FitFlow | Trade off |
|---|---|---|
| Node.js with Express | Rapid API development; matches the case study | Keep CPU-intensive inference out of the API process |
| Node.js with NestJS | Structured modules for a growing team | More framework setup initially |
| Python with FastAPI | Natural fit for model-serving and Python ML | Another service language and integration boundary |
| Go | Efficient concurrent services | More initial effort for a JS and Python team |

**Recommendation:** Express for application APIs. Use FastAPI only for the separate cloud AI service when needed.

## Database options

| Option | Scalability and query fit | Health and fitness data fit |
|---|---|---|
| PostgreSQL | Joins, transactions and indexed reports; scaling depends on deployment | Source of truth for profiles, workouts and nutrition |
| MongoDB | Flexible documents and aggregation; careful indexing required | Useful for flexible content, but reporting needs deliberate modeling |
| Cloud Firestore | Managed scale and live listeners; usage costs must be watched | Restricted social feed and challenge data |
| DynamoDB | Managed scaling with planned access patterns | More modeling effort when relationships and reports change |

**Recommendation:** PostgreSQL for structured sensitive records; Firestore only for community content that needs live updates. Avoid copying private health records into social posts.

## Authentication and authorization options

| Option | Strength | FitFlow consideration |
|---|---|---|
| Firebase Authentication | Mobile and browser sign-in; integrates with Firestore rules | Verify tokens in the API; implement app roles separately |
| AWS Cognito | Managed identity and AWS integration | More setup outside an AWS-centered stack |
| Auth0 | Flexible identity and federation | Evaluate provider cost and integrations |
| Supabase Auth | Convenient for Postgres-centered development | Requires a different real-time design |

**Recommendation:** Firebase Authentication. The API must verify ID tokens and authorize records; Firestore rules must restrict circle membership. Compliance with GDPR or HIPAA is not automatic: assess the actual deployment, consent, data handling, agreements and applicable laws.

## Sources

- React Native platforms: https://reactnative.dev/docs/out-of-tree-platforms
- Flutter platforms: https://docs.flutter.dev/reference/supported-platforms
- Kotlin Multiplatform: https://kotlinlang.org/docs/multiplatform.html
- SwiftUI: https://developer.apple.com/swiftui/
- Express: https://expressjs.com/en/guide/routing.html
- FastAPI: https://fastapi.tiangolo.com/features/
- PostgreSQL row security: https://www.postgresql.org/docs/current/ddl-rowsecurity.html
- Firestore: https://firebase.google.com/docs/firestore
- Firebase Authentication: https://firebase.google.com/docs/auth
- Firestore security: https://firebase.google.com/docs/firestore/security/overview
- Firebase privacy: https://firebase.google.com/support/privacy
