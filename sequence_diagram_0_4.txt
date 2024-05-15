sequenceDiagram
    
    participant browser
    participant server

    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML DOCUMENT
    deactivate server

    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS FILE
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JS FILE: main.js
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: DATA: [{content: "hi", date: "2024-05-14T20:18:36.264Z"},…]
    
    deactivate server
    
    Note right of browser: The browser executes the callback function that renders the notes

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note | note: Hi from Venezuela
    activate server
    Note left of server: The server adds the new note to the database 
    server-->>browser: HTTP REDIRECT : STATUS CODE 302  
    deactivate server

    
  
    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML DOCUMENT
    deactivate server

    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS FILE
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JS FILE: main.js
    deactivate server

     Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: DATA: [{content: "hi", date: "2024-05-14T20:18:36.264Z"},…]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
