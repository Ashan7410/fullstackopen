sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user writes "add for full stack" in the input field
    Note right of browser: The user clicks the "Save" (submit) button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of browser: Form data: { note: "add for full stack" }
    activate server
    Note left of server: The server creates a new note object
    Note left of server: The server adds the new note to the data array
    server-->>browser: HTTP status code 302 Found (Redirect to /notes)
    deactivate server

    Note right of browser: The 302 redirect causes the browser to reload the notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ..., { "content": "add for full stack", "date": "2023-x-y" } ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes, including the new one
