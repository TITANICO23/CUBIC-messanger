# CUBIC-messanger

<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Editor di Testo con Salvataggio Automatico</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .editor-container {
            width: 80%;
            max-width: 800px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
        }
        textarea {
            width: 100%;
            height: 300px;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 10px;
            font-size: 16px;
            box-sizing: border-box;
            resize: none;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        .status {
            text-align: right;
            font-size: 12px;
            color: #888;
        }
    </style>
</head>
<body>

    <div class="editor-container">
        <h1>Editor di Testo con Salvataggio Automatico</h1>
        <textarea id="editor" placeholder="Scrivi qualcosa..."></textarea>
        <div class="status" id="status">Salvataggio in corso...</div>
    </div>

    <script>
        // Recupera l'elemento textarea e il messaggio di stato
        const editor = document.getElementById("editor");
        const status = document.getElementById("status");

        // Funzione per caricare il testo salvato
        function loadText() {
            const savedText = localStorage.getItem("savedText");
            if (savedText) {
                editor.value = savedText;
            }
        }

        // Funzione per salvare automaticamente il testo
        function saveText() {
            const text = editor.value;
            localStorage.setItem("savedText", text);
            status.textContent = "Testo salvato automaticamente!";
        }

        // Carica il testo salvato al caricamento della pagina
        loadText();

        // Aggiungi un evento che salva il testo ogni volta che l'utente scrive
        editor.addEventListener("input", function() {
            saveText();
        });

        // Aggiungi un breve delay per il messaggio di salvataggio automatico
        editor.addEventListener("input", function() {
            setTimeout(() => {
                status.textContent = "Salvato!";
            }, 100);
        });
    </script>

</body>
</html>
