sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document (SPA container)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file (SPA version)
    deactivate server

    Note right of browser: The browser starts executing the specific SPA JavaScript code that fetches the initial notes JSON from the server.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "SPA rendering is efficient", "date": "2023-11-05" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function in spa.js that renders the notes on the client, updating the DOM dynamically without reloading the entire page.
