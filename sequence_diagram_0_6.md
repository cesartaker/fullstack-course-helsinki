sequenceDiagram
    
    participant browser
    participant server

    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML DOCUMENT
    deactivate server

    browser->>server:GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS FILE
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JS FILE: spa.js
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: DATA: [{content: "hi", date: "2024-05-14T20:18:36.264Z"},…]
    deactivate server
    
    Note right of browser: The browser executes the callback function that renders the notes

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa | note: Arepa's World
    activate server
    Note left of server: The server adds the new note to the database and update the page 
    server-->>browser: RESPONSE: STATUS CODE 201 || {"message":"note created"}
    deactivate server

    