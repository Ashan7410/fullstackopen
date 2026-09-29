sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user writes a note in the text field and clicks the Save button
    Note right of browser: The event handler in the JavaScript prevents the default form submission

    Note right of browser: The browser locally creates the new note, adds it to the notes list, and redraws the notes on the screen

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: Request payload (JSON): { "content": "single page app note", "date": "2026-09-28" }
    activate server
    
    Note left of server: The server processes the JSON data and saves the new note
    
    server-->>browser: HTTP status code 201 Created
    deactivate server
    
    Note right of browser: The browser stays on the current page. No further HTTP requests are made.
