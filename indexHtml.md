# SEO, accessibilité et bonnes pratiques

- Remplacer les **urlsite** et *** par les bonnes informations

- **js** pour Svelte, **jsx** pour React

```html
<!doctype html>
<html lang="fr">
	<head>
		<!-- Meta généraux au site + title -->
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<meta name="description" content="***" />
		<meta name="robots" content="index, follow">
		<title>***</title>

		<!-- Favicon -->
		<link rel="icon" type="image/svg+xml" href="/***.svg" />
		<link rel="icon" type="image/x-icon" href="/***.ico">

		<!-- Open Graph : partage sur réseaux sociaux -->
		<meta property="og:title" content="***">
		<meta property="og:description" content="***" />
		<meta property="og:image" content="https://urlsite/***.png">
		<meta property="og:url" content="https://urlsite/">
		<meta property="og:type" content="website">
		<meta property="og:locale" content="fr_FR"> 
		
		<!-- Twitter Card -->
		<meta name="twitter:card" content="summary_large_image">
		<meta name="twitter:title" content="***">
		<meta name="twitter:description" content="***" />
		<meta name="twitter:image" content="https://urlsite/***.png">
		
		<!-- Localisation géographique -->
		<meta name="geo.region" content="FR-***">
		<meta name="geo.placename" content="***">
		<meta name="geo.position" content="***"> 
		
		<!-- Informations générales -->
		<meta name="author" content="***">
		<meta name="publisher" content="***">

    <!-- Identité du site (utile pour SEO et accessibilité) -->
    <meta name="application-name" content="***">
    <meta name="apple-mobile-web-app-title" content="***">

    <!-- Apparence navigateur (utile pour expérience utilisateur) || couleur de la barre de navigation sur mobile -->
    <meta name="theme-color" content="#***">
    <meta name="msapplication-TileColor" content="#***">

    <!--  Favicon / icônes (important visuellement) || icône quand on enregistre ton site sur le téléphone, ou sur un onglet navigateur -->
    <link rel="shortcut icon" href="/***.ico">
    <link rel="apple-touch-icon" href="/***.png">
    <meta name="icon" sizes="192x192" href="/***.png">
    <meta name="icon" sizes="512x512" href="/***.png">
    <meta name="icon" sizes="any" type="image/svg+xml" href="/***.svg">
    <!-- Icône personnalisée pour Safari (barre d'onglets). -->
    <link rel="mask-icon" href="/WA.svg" color="#***">

    <!-- Permet à ton site d’être installé comme une app sur iOS/Android. -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

    <!-- PWA (installation sur mobile, etc.) || msapplication-... sont spécifiques à Windows (Edge/ancien Windows Phone) -->
    <link rel="manifest" href="/manifest.webmanifest">
    <meta name="msapplication-TileImage" content="/***.png">
    <meta name="msapplication-config" content="/browserconfig.xml">

		<!-- Données structurées : Service Web -->
		<script type="application/ld+json">
			{
				"@context": "https://schema.org",
				"@type": "ProfessionalService",
				"name": "***",
				"image": "https://urlsite/***.png",
				"description": "***",
				"address": {
					"@type": "PostalAddress",
					"addressLocality": "***",
					"postalCode": "***",
					"addressCountry": "FR"
				},
				"telephone": "+33***",
				"url": "https://urlsite/",
				"sameAs": [
					"https://www.linkedin.com/in/nom/"
				]
			}
		</script>
	
		<!-- Données structurées : Organisation -->
		<script type="application/ld+json">
			{
				"@context": "https://schema.org",
				"@type": "Organization",
				"name": "***",
				"url": "https://urlsite/",
				"logo": "https://urlsite/***.png"
			}
		</script>
		
	</head>
	<body>
		<div id="root" role="main"></div>
		<script type="module" src="/src/main.jsx"></script> 
	</body>
</html>

```
