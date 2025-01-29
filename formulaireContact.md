# Formulaire  de contact avec Svelte

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
    // téléphone
    function formatPhoneNumber() {
        let value = telInput.value.replace(/\D/g, ''); // Supprime tout les caractères numériques
        if (value.length > 10) value = value.slice(0, 10); // Limite la longueur du numéro à 10 chiffres
        tel = value.replace(/(\d{2})(?=\d)/g, '$1.'); // Applique le format souhaité à savoir un point tout les deux chiffres
    }

    // email
    function validateEmail() {
        // vérifie la validité d'une adresse email en respectant les règles suivantes :
        // - La partie avant le @ peut contenir des lettres, chiffres et certains caractères spéciaux (., _, %, +, -).
        // - Un seul @ est autorisé, suivi par le nom de domaine (lettres, chiffres, tirets, et points).
        // - L'email doit se terminer par un TLD valide (ex. .com, .fr) contenant au moins 2 lettres.
        const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        if (!emailRegex.test(email)) {
        errorMessage = "Veuillez entrer une adresse email valide : exemple@gmail.com";
        } else {
        errorMessage = '';
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

### La function du formulaire de contact

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
