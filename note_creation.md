# Note Creation Flow

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server
    participant Database

    User->>Browser: Writes text in the input field
    User->>Browser: Clicks "Save" button

    Browser->>Server: POST /notes with note data
    Server->>Database: INSERT new note data
    Database->>Server: Note saved confirmation
    Server->>Browser: Sends response with the new note data
    Browser->>User: Displays the new note in the notes list

    note right of Browser: Browser collects the input text and sends POST request to the server
    note right of Server: Server receives the POST request, processes it, and prepares to save the note
    note right of Database: Database stores the new note and confirms the save
    note right of Server: Server prepares and sends the response with the new note data back to the browser
    note right of Browser: Browser receives the response and updates the UI with the new note
