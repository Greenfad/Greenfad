<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hôtel L'Amitié</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            margin: 0;
            padding: 0;
            color: #333;
        }

        #logo {
            max-width: 200px;
            max-height: 200px;
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
            margin-top: 20px;
            animation: rotateLogo 3s infinite linear;
        }

        @keyframes rotateLogo {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        #hotel-info {
            margin: 20px;
            padding: 10px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }

        .button {
            padding: 15px 30px;
            margin: 10px;
            cursor: pointer;
            background-color: #28a745;
            color: #fff;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            transition: background-color 0.3s ease, transform 0.3s ease;
        }

        .button:hover {
            background-color: #218838;
            transform: scale(1.05);
        }

        #message-container {
            background-color: #28a745;
            padding: 20px;
            margin: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            color: #fff;
            font-size: 18px;
        }

        #footer {
            background-color: #333;
            color: #fff;
            padding: 10px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        #room-number {
            padding: 10px;
            margin: 10px;
            font-size: 16px;
            width: 50%;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
    </style>
    <script>
        function redirectToWhatsApp(action) {
            var phoneNumber = "NuméroWhatsApp"; // Remplacez par le vrai numéro WhatsApp
            var roomNumber = document.getElementById("room-number").value;

            if (roomNumber !== null && roomNumber.trim() !== "") {
                var message = "Salut, je suis dans la chambre " + roomNumber + ". ";

                if (action === 'clean') {
                    message += "J'aimerais faire ma chambre.";
                } else if (action === 'do-not-disturb') {
                    message += "Ne pas déranger la chambre " + roomNumber + ".";
                } else if (action === 'need-waiter') {
                    message += "J'ai besoin d'une serveuse dans la chambre " + roomNumber + ".";
                } else if (action === 'invite') {
                    message += "Je t'invite à rejoindre notre groupe WhatsApp de l'hôtel.";
                }

                var whatsappURL = "https://wa.me/" + phoneNumber + "?text=" + encodeURIComponent(message);
                document.getElementById("message-container").innerText = message;
                window.location.href = whatsappURL;
            }
        }
    </script>
</head>
<body>
    <div id="hotel-info">
        <img id="logo" src="chemin/vers/votre-logo.png" alt="Logo de l'hôtel">
        <h1>Hôtel L'Amitié</h1>
        <p>Adresse de l'hôtel | Autre information pertinente</p>
    </div>

    <label for="room-number">Numéro de chambre :</label>
    <input type="text" id="room-number" placeholder="Entrez le numéro de chambre">

    <!-- Boutons existants -->
    <button class="button" onclick="redirectToWhatsApp('clean')">Faites ma chambre</button>
    <button class="button" onclick="redirectToWhatsApp('do-not-disturb')">Ne pas déranger</button>
    <button class="button" onclick="redirectToWhatsApp('need-waiter')">Besoin d'une serveuse</button>

    <!-- Bouton d'invitation direct vers le groupe WhatsApp -->
    <button class="button" onclick="redirectToWhatsApp('invite')">Inviter à rejoindre le groupe WhatsApp</button>

    <div id="message-container"></div>

    <div id="footer">
        © 2023 Hôtel L'Amitié. Tous droits réservés.
    </div>
</body>
