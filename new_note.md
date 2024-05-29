# Creating a New Note in SPA

```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server
    participant Database

    User->>Browser: Types a note in the input field
    User->>Browser: Clicks "Save" button

    note right of Browser: Browser collects the input text and prepares the POST request

    Browser->>Server: HTTP POST /new_note with note data
    note right of Server: Server receives the POST request
    Server->>Database: Insert new note data into database
    note right of Database: Database stores the new note and confirms
    Database->>Server: Confirmation of note saved
    note right of Server: Server prepares the response with the new note data
    Server->>Browser: Sends response with the new note data

    note right of Browser: Browser receives the response and updates the UI
    Browser->>User: Displays the new note in the notes list
