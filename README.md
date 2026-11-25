PlantIQ


An AI-powered platform for South Indian coffee farmers that brings
together coffee-leaf disease detection, evidence-grounded agricultural
guidance, local weather insights, bilingual voice assistance, and a
farmer-to-buyer marketplace.

PlantIQ is designed to help coffee farmers make more informed decisions
through an accessible web and Android experience.
Key Features
1. AI-Powered Coffee Leaf Disease Detection
- Upload or capture a coffee leaf image using the camera or gallery.
- Classify the detected disease using the ResNet-50 model.
- Display prediction confidence and class probabilities.
- Provide a low-confidence notice when the model is uncertain.
- Connect the scan result to relevant advisory guidance and chat.
2. Grounded Agricultural Advisory
- Uses a hybrid Retrieval-Augmented Generation (RAG) pipeline over
  coffee-related CCRI documents.
- Combines dense and keyword retrieval, reciprocal-rank fusion,
  reranking, and near-duplicate removal.
- Generates practical treatment guidance with supporting source
  references.
- Uses Gemini and Groq as model providers, with an offline fallback
  path.
- Includes weather context when generating recommendations.
3. Weather-Aware Insights
- Uses estate coordinates from GPS or manually entered locations.
- Retrieves weather information through Open-Meteo.
- Displays current conditions and a short forecast.
- Provides disease-risk context and suggested spray windows where
  supported by the available weather data.
4. Bilingual Chat and Voice
- Supports English and Kannada.
- Provides conversational access to agricultural guidance.
- Supports voice input and speech-to-text integrations.
- Allows users to ask follow-up questions and share scan context.
5. Coffee Marketplace
- Lets farmers create coffee listings with quantity, unit, price,
  photos, and location.
- Supports search, sorting, and filters.
- Helps buyers discover nearby listings and contact sellers through
  call or WhatsApp.
- Includes route/navigation hand-off and listing management.
6. Farmer Account and History
- Account registration and sign-in using supported identifiers.
- Profile and password management.
- Server-side scan history with filtering and record management.
- English/Kannada interface, themes, and dark mode.
Technology Stack
  Layer                               Technologies
  Backend/API                         Python, FastAPI

  Database/ORM                        SQLAlchemy, PostgreSQL or SQLite

  Disease detection                   ResNet-50

  Retrieval pipeline                  BGE-M3, BM25, Reciprocal Rank
Fusion (RRF), BGE reranker

  LLM providers                       Gemini, Groq

  Weather                             Open-Meteo

  Frontend                            React 18, TypeScript, Vite

  Android                             Capacitor 7
Speech                              IndicConformer / Svarah Whisper STT
Architecture Overview
Web app (React + TypeScript)       Android app (Capacitor)
              \                         /
               \                       /
                 ------ FastAPI --------
                         |
       -----------------------------------------
       |          |           |                |
   ResNet-50   Hybrid RAG   Weather API     Marketplace
   inference   retrieval    (Open-Meteo)    + accounts
                  |
          CCRI reference documents
                  |
         Gemini / Groq / offline
The web frontend and Android wrapper communicate with the FastAPI
backend. The backend coordinates image inference, retrieval-based
advisory generation, weather lookups, user data, and marketplace
operations.
Repository Structure
.
├── backend/       # FastAPI services, models, database and application logic
├── frontend/      # React + TypeScript web application
├── mobile/        # Capacitor Android wrapper
├── design/        # Design system and mockups
├── scripts/       # Run, sync, test and build scripts
├── docs/          # Architecture, modules, user flows and deployment guides
├── release/       # Android release artifact (if included in the checkout)
└── og/            # Earlier application version retained for reference
