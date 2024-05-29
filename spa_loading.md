# SPA Loading Flow

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server
    participant Database

    User->>Browser: Opens https://studies.cs.helsinki.fi/exampleapp/spa
    Browser->>Server: HTTP GET /spa
    Server->>Browser: Sends HTML for SPA

    note right of Browser: Browser loads the HTML file, which includes references to CSS and JavaScript files

    Browser->>Server: HTTP GET /main.js
    Server->>Browser: Sends main.js

    Browser->>Server: HTTP GET /style.css
    Server->>Browser: Sends style.css

    note right of Browser: Browser executes main.js which contains the SPA logic

    Browser->>Server: HTTP GET /data.json
    Server->>Database: Request to fetch notes data
    Database->>Server: Sends notes data
    Server->>Browser: Sends notes data as JSON

    note right of Browser: Browser receives the notes data and updates the UI

    Browser->>User: Displays the notes in the SPA
