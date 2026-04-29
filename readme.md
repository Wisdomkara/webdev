## 0.5 SPA Load Flow

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant WebServer
    participant SPA
    participant API
    participant Database

    User->>Browser: Open SPA URL
    Browser->>WebServer: GET /spa
    WebServer-->>Browser: HTML + JS

    Browser->>SPA: Execute JS
    SPA->>API: GET /api/notes
    API->>Database: Fetch notes
    Database-->>API: Return data
    API-->>SPA: JSON response
    SPA-->>Browser: Render UI

    
---

```markdown
## 0.6 Create New Note (SPA)

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant SPA
    participant API
    participant Middleware
    participant Database

    User->>Browser: Submit new note
    Browser->>SPA: Form event intercepted
    SPA->>API: POST /api/notes

    API->>Middleware: Validate request
    Middleware-->>API: OK

    API->>Database: Save note
    Database-->>API: Confirm insert

    API-->>SPA: Return JSON
    SPA-->>Browser: Update UI