```mermaid

sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser executes the JavaScript code of the single-page app

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The user types a new note and submits it via the form

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note<br>Content-Type: application/json<br>{ "content": "A new note", "date": "2024-11-20" }
    activate server
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: The app updates the local data model with the new note<br>and re-renders the notes list dynamically
