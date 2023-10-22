<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            background-color: #333;
            color: #fff;
            font-size: 18px;
            text-align: center;
            padding-top: 20px;
        }

        #chat {
            max-width: 800px;
            margin: 0 auto;
        }

        #messages {
            padding: 10px;
            margin-bottom: 10px;
            max-height: 300px;
            overflow-y: auto;
            border: 1px solid #777;
            border-radius: 5px;
        }

        #message {
            width: 80%;
            padding: 10px;
            font-size: 16px;
        }

        #send-button {
            background-color: #0074D9;
            color: #fff;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
        }

        .user-message {
            font-weight: bold;
            color: #0074D9;
        }

        /* Animación para resaltar mensajes */
        @keyframes highlight {
            0% {
                background-color: transparent;
            }
            50% {
                background-color: #0074D9;
            }
            100% {
                background-color: transparent;
            }
        }

        .highlighted-message {
            animation: highlight 2s;
        }

        /* Estilos para la sección de mensajes privados */
        #private-messages {
            position: fixed;
            bottom: 10px;
            right: 10px;
            width: 250px;
            background-color: #f0f0f0;
            border: 1px solid #ccc;
            padding: 10px;
            overflow-y: scroll;
            max-height: 150px;
        }

        /* Estilos para el botón de mensajes privados */
        #send-private-button {
            background-color: red;
            color: #fff;
            border: none;
            padding: 5px 10px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div id="chat">
        <input type="text" id="username" placeholder="Nombre de usuario">
        <button id="set-username">Establecer Nombre de Usuario</button>
        <h1>AnonyChat Alpha</h1>
        <div id="messages"></div>
        <input type="text" id="message" placeholder="Escribe un mensaje">
        <button id="send-button">Enviar</button>
        <input type="text" id="private-recipient" placeholder="Usuario destinatario">
        <button id="send-private-button">Enviar Privado</button>
    </div>

    <!-- Sección de mensajes privados -->
    <div id="private-messages">
        <h2>Mensajes Privados</h2>
        <ul id="private-messages-list"></ul>
    </div>
    <script>
        var username = "";

        function eliminarMensaje(event) {
            var div = event.target.parentNode; // Obtiene el div que contiene el mensaje
            div.parentNode.removeChild(div); // Elimina el div que contiene el mensaje
        }

        function setUsername() {
            var usernameInput = document.getElementById("username");
            var usernameValue = usernameInput.value;
            if (usernameValue.trim() !== "") {
                username = usernameValue;
                usernameInput.disabled = true;
            }
        }

        document.getElementById("set-username").addEventListener("click", setUsername);

        function enviarMensaje() {
            var mensaje = document.getElementById("message").value;
            if (mensaje.trim() !== "") {
                var div = document.createElement("div");
                div.innerHTML = "<span class='user-message'>" + username + ":</span> " + mensaje;

                // Agregar un botón de eliminación
                var deleteButton = document.createElement("button");
                deleteButton.innerHTML = "Eliminar";
                deleteButton.addEventListener("click", eliminarMensaje);
                div.appendChild(deleteButton);

                div.classList.add("highlighted-message");
                document.getElementById("messages").appendChild(div);
                document.getElementById("message").value = "";
            }
        }

        document.getElementById("send-button").addEventListener("click", enviarMensaje);

        document.getElementById("message").addEventListener("keydown", function(event) {
            if (event.key === "Enter") {
                enviarMensaje();
            }
        });

        function recibirMensajePrivado() {
            var mensaje = document.getElementById("message").value;
            var destinatario = document.getElementById("private-recipient").value;
            if (mensaje.trim() !== "" && destinatario.trim() !== "") {
                var div = document.createElement("div");
                div.innerHTML = "<span class='user-message'>" + username + " ➔ " + destinatario + ":</span> " + mensaje;

                div.classList.add("highlighted-message");
                document.getElementById("messages").appendChild(div);
                document.getElementById("message").value = "";
                document.getElementById("private-recipient").value = "";

                // Agregar el mensaje privado a la sección de mensajes privados
                var privateMessagesList = document.getElementById("private-messages-list");
                var privateMessageItem = document.createElement("li");
                privateMessageItem.textContent = "De: " + username + " ➔ " + destinatario + ": " + mensaje;
                privateMessagesList.appendChild(privateMessageItem);
            }
        }

        document.getElementById("send-private-button").addEventListener("click", recibirMensajePrivado);
    </script>
</body>
</html>
