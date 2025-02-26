# Formulaire  de contact avec Svelte

 1. GMAIL
    
## Dans le script 

### Définir nos variables

```svelte
const formEndpoint = import.meta.env.VITE_FORM_ENDPOINT;

let demande = "information";
    let urgence = "oui";
    let localisation = "Montpellier";
    let nom = "";
    let tel = "";
    let telInput;
    let email = "";
    let commentaire = "";
    let errorMessage = "";
    let successMessage = "";
```

### Définir nos validations, de mail, téléphone et texte

```svelte
    // Téléphone
    let errorMessageTel = '';

    function formatPhoneNumber(event) {
        let value = event.target.value.replace(/\D/g, ''); // Supprime tout sauf les chiffres
        if (value.length > 10) value = value.slice(0, 10); // Limite à 10 chiffres

        // Applique le format : "01.23.45.67.89"
        value = value.replace(/(\d{2})(?=\d)/g, '$1.');

        // Met à jour l'input via event.target.value (évite les bugs avec bind:value)
        event.target.value = value;
        tel = value; // Met à jour la variable Svelte
    }

    function validatePhone() {
        const phoneRegex = /^0[1-9](\.[0-9]{2}){4}$/;
        errorMessageTel = phoneRegex.test(tel) ? "" : "Le numéro doit être au format 01.02.03.04.05";
    }

    // Email
    let errorMessageMail = '';
    
    function validateEmail() {
        // vérifie la validité d'une adresse email en respectant les règles suivantes :
        // - La partie avant le @ peut contenir des lettres, chiffres et certains caractères spéciaux (., _, %, +, -).
        // - Un seul @ est autorisé, suivi par le nom de domaine (lettres, chiffres, tirets, et points).
        // - L'email doit se terminer par un TLD valide (ex. .com, .fr) contenant au moins 2 lettres.
        if (email && !/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(email)) {
            errorMessageMail = "Veuillez entrer une adresse email valide : exemple@gmail.com";
        } else {
            errorMessageMail = '';  // Si l'email est valide ou non renseigné, on efface l'erreur
        }
    }

    // Taille du textarea de commentaire
    let textarea;

    function adjustSize() {
        if (textarea) {
        textarea.style.height = 'auto';
        textarea.style.height = `${textarea.scrollHeight}px`;
        }
    }

    onMount (() => {
        adjustSize();
    });
```

### La fonction du formulaire de contact

```svelte
    async function sendForm(event) {
        event.preventDefault();

        const formData = {
            demande,
            urgence,
            localisation,
            nom,
            tel,
            email,
            commentaire,
        };

        // console.log("Sending form data:", formData);
        
        try {
            const response = await fetch(formEndpoint, {
                method: "POST",
                headers: {
                "Content-Type": "application/json",
                },
                body: JSON.stringify(formData),
            });

            console.log("Response received from server:", response);

            const result = await response.json();
            console.log("Server response parsed:", result);

            if (result.success) {
                successMessage = "Votre message a été envoyé avec succès !";
                errorMessage = "";
            } else {
                errorMessage = "Une erreur est survenue.";
                successMessage = "";
            }
        } catch (error) {
            errorMessage = "Erreur lors de l'envoi.";
            console.log("Error during form submission:", error);
            successMessage = "";
        }
    }
```

## Dans le HTML 

### Mettre les bind:... sur les imput

```bind:group={urgence}``` (pour les type radio)
```bind:value={localisation}``` (pour les type radio)

### Mettre le on:submit dans le form

``` Svelte
  <form action="" method="post" on:submit|preventDefault={sendForm}>
```

### Mettre les messages  de succès et d'erreur en fin de formulaire

``` Svelte
  {#if successMessage}
      <p style="color: green;">{successMessage}</p>
  {/if}
  {#if errorMessage}
      <p style="color: red;">{errorMessage}</p>
  {/if}
```

## Dans notre pc

### Télécharger xampp

- Aller dans le dossier de Xampp
- Puis dans le dossier htdocs
- Créer un dossier du nom du projet
- Dans ce dossier du nom de notre projet, créer un fichier send-mail.php
- Dans XAMPP puis Config  puis php.ini  :
  -  ```SMTP=smtp.gmail.com``` : si utilisation de gmail
  -  ```smtp_port=587``` : pour gmail
  -  ```sendmail_from = example@gmail.com``` : Mettre le mail de l'entreprise

### Télécharger composer PHP

Dans le terminal mettre les commandes :
-   ```sudo apt install composer``` : Installation de composer
-   ```composer --version``` : Véfifier la version

### Télécharger PHPMailer

- Se mettre dans le dossier de notre projet dans XAMPP
- ```composer require phpmailer/phpmailer``` : Installation de PHPMailer

### L'entreprise ou la personne qui dois recevoir les mail du formulaire

- Se connecter au compte mail
- Paramètre de  sécurité
- Activer l'authentification à deux facteurs
- Dans la barre de recherche : Mots de passe d'application
- Dans le menu déroulant séléctionner : Autre (nom personnalisé)
- Donner un nom comme "PHPMailer" ou "Serveur local"
- On reçoit un mot de passe à coller dans le send-mail.php
- 
Le mot de passe d'application permet de se connecter à ton compte Google sans exposer ton mot de passe réel. C'est une mesure de sécurité supplémentaire, qui empêche des applications non sécurisées ou non autorisées d'accéder à ton compte Gmail directement.

2. OUTLOOK / Mailjs

## Dans le terminal de notre projet

Faire la commande : ```npm install emailjs-com```

## Dans le script 

```svelte
import emailjs from "emailjs-com"
```

### Définir nos variables

```svelte
let nom = "";
    let email = "";
    let tel = "";
    let demande = "information";
    let urgence = "";
    let localisation = "Montpellier";
    let commentaire = "";
    let errorMessage = "";
    let errorMessageForm = '';
    let errorMessageTelMail = '';
```

### La fonction du formulaire de contact

```svelte
function envoyerFormulaire() {
        
      if (!email && !tel) {
          errorMessageTelMail = "Veuillez entrer au moins un email ou un numéro de téléphone.";
          console.log(errorMessageTelMail);
          return;
      } else {
          errorMessageTelMail = ''; // Si la condition est remplie, on vide le message d'erreur
      }
      
      // Vérification du format du téléphone avant l'envoi
      if (tel && !/^0[1-9](\.[0-9]{2}){4}$/.test(tel)) {
          errorMessage = "Le numéro de téléphone doit être au format 01.02.03.04.05";
          return;
      }
   
      // Si l'email est renseigné, on vérifie sa validité
      if (email && !/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(email)) {
          errorMessageMail = "Veuillez entrer une adresse email valide.";
          return;
      } else {
          errorMessageMail = '';  // Réinitialise le message d'erreur pour l'email
      }
   
      // Informations à envoyer
      let templateParams = {
          to_email: "lemail@outlook.com", // Remplacez par votre e-mail
          nom,
          email,
          tel,
          demande,
          urgence,
          localisation,
          commentaire
      };
   
      // Envoi via EmailJS
      emailjs
          .send(
              "service_azerty",
              "template_aze123",
              templateParams,
              "aZe1R2t3Y"
          )
          .then(
              function (response) {
                  alert("Formulaire envoyé avec succès !");
                  console.log("SUCCESS!", response.status, response.text);
              },
              function (error) {
                  alert("Échec de l'envoi.");
                  console.log("FAILED...", error);
              }
          );
    }
```

### Mettre le on:submit dans le form

``` Svelte
  <form on:submit|preventDefault={envoyerFormulaire}>
```

### Mettre les message d'erreur dans le form

``` Svelte
  {#if errorMessageTel}
      <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageTel}</p>
  {/if}
```
``` Svelte
  {#if errorMessageMail}
      <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageMail}</p>
  {/if}
```
``` Svelte
 {#if errorMessageTelMail}
     <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageTelMail}</p>
 {/if}
```
``` Svelte
 <button type="submit" disabled={!!errorMessageForm}>Envoyer</button>
```

## Sur le site de Mailjs

- Se rendre sur EmailJS et crée un compte  : https://www.emailjs.com/
- Ajouter un service email avec le compte Outlook.
- Créer un template d'email avec les champs qu'on veut envoyer

### Le template

Exemple :

``` HTML
<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            color: #333;
        }
        .container {
            max-width: 600px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 10px;
            background: #f9f9f9;
        }
        h2 {
            color: #0056b3;
        }
        .info {
            padding: 10px;
            background: #ffffff;
            border-radius: 5px;
            margin-bottom: 10px;
            box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
        }
        .message {
            font-style: italic;
            color: #444;
            background: #fffbe6;
            padding: 10px;
            border-left: 3px solid #f5b400;
        }
        .footer {
            margin-top: 20px;
            text-align: center;
            font-size: 12px;
            color: #666;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Nouvelle Demande de Contact</h2>
        <p>Bonjour,</p>
        <p>Vous avez reçu une nouvelle demande via le formulaire de contact. Voici les détails :</p>

        <div class="info">
            <strong>👤 Nom :</strong> {{nom}}<br>
            <strong>📧 E-mail :</strong> {{email}}<br>
            <strong>📞 Téléphone :</strong> {{tel}}<br>
            <strong>🚗 Objet :</strong> {{demande}}<br>
        </div>

        <div class="message">
            <strong>✏️ Message :</strong><br>
            "{{commentaire}}"
        </div>

        <p>Merci de prendre contact avec cette personne dès que possible.</p>

        <div class="footer">
            <p>📌 Cet e-mail a été généré automatiquement par votre site web.</p>
        </div>
    </div>
</body>
</html>
```

### Les données qu'il faut rentrer dans le code

- Service ID : Disponible sur l'onglet Email Services.
- Template ID : Va dans Email Templates et copie ton template ID.
- Public Key : Disponible dans la section Account.



