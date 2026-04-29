# Part 0 – SPA Diagrams

## 0.5 SPA Load Flow

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant WebServer
    participant SPA
    participant API
    participant Database

    User->>Browser: Open SPA URL (notes app)
    Browser->>WebServer: GET /spa
    WebServer-->>Browser: HTML + JavaScript bundle

    Browser->>SPA: Execute JavaScript (boot app)

    SPA->>API: GET /api/notes
    API->>Database: Fetch notes
    Database-->>API: Return notes
    API-->>SPA: JSON response

    SPA-->>Browser: Render notes UI
    Browser-->>User: Display notes (no page reload)