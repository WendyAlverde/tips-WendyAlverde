# Accéder au serveur local sur le téléphone

## Utilisation de ngrok

**ngrok** est un outil qui crée des tunnels sécurisés entre un serveur local (comme votre machine) et une URL publique accessible sur Internet. Il est idéal pour partager votre site en cours de développement ou tester des intégrations web sans avoir besoin de déployer le site sur un serveur distant.

### Installation de ngrok

1. Aller sur le site de ngrok : [https://dashboard.ngrok.com/get-started/setup/windows](https://dashboard.ngrok.com/get-started/setup/windows)
2. Choisir son environnement de travail (par exemple, Windows).
3. Cliquer sur **Download**
4. Extraire le fichier du zip.
5. Ouvrir le fichier `.exe` cela ouvre un terminal (invite de commande).
6. Sur ce terminal, entrez la commande suivante pour configurer votre jeton d'authentification (remplacez le jeton si nécessaire) :
   ```bash
   ngrok config add-authtoken 2rwPVd0Klf3AkrmP8DoYG9Q4YFg_6XiG3uRvvkpBhDS1WiCG9

### Utilisation de ngrok

1. Ouvrir un terminal dans le dossier de votre projet.
2. Lancer le serveur local. Par exemple, si vous utilisez Svelte, exécutez :
   ```bash
   npm run dev
3. Ouvrir le terminal de ngrok (le fichier .exe).
4. Lancer ngrok en indiquant l'URL locale de votre serveur. Adaptez le port selon celui utilisé par votre projet (ici, 5173 est l'exemple pour Svelte) :
   ```bash
   ngrok http http://localhost:5173
5. ngrok affichera une URL publique dans son terminal, par exemple :
   ```bash
   Forwarding    https://random-subdomain.ngrok.io -> http://localhost:5173
6. Copiez l'URL publique (commençant par https://) et ouvrez-la dans le navigateur de votre téléphone.

Assurez-vous que votre téléphone est connecté au même réseau que votre PC si vous voulez un accès rapide et fluide.
