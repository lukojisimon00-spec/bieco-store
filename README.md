# Bieco Store

Boutique en ligne de Bieco Production (Kinshasa) : produits agroalimentaires et formations.

Site en ligne : <https://bieco-store.vercel.app>

## Contenu

- `index.html` : le site (une seule page, mobile-first).
- `images/fufu-express.jpg` : photo du produit vedette (sortie du HTML pour alléger la page).

## État actuel

- Les commandes sont préparées sur la page puis envoyées par **WhatsApp** au +243 894 963 392.
- **Aucun paiement n'est encaissé en ligne** pour l'instant.

## Mise en ligne sur Vercel (une seule fois)

1. Ouvrir <https://vercel.com> et se connecter avec GitHub.
2. « Add New… » → « Project » → choisir le dépôt `bieco-store` → « Import ».
3. Framework Preset : **Other**. Ne rien changer d'autre → « Deploy ».
4. Vercel donne une adresse du type `bieco-store.vercel.app`. Chaque modification
   envoyée sur GitHub met le site à jour automatiquement.

## Paiement Mobile Money / banque (étape suivante)

Le paiement réel demande un **serveur** (fonctions Vercel dans `api/`), car les clés
secrètes de l'opérateur ne doivent jamais apparaître dans `index.html`.

Règles :
- Les clés sont enregistrées uniquement dans Vercel → Settings → Environment Variables.
- Le site ne demande jamais de code PIN ni de code OTP : le client confirme sur son téléphone,
  via le message de l'opérateur.
- Ne jamais saisir un numéro de carte bancaire sur ce site : utiliser la page de paiement
  hébergée par la banque ou l'opérateur.
- Une commande n'est « payée » que si le serveur reçoit la confirmation de l'opérateur
  (callback), jamais sur la seule parole de la page.
- On développe d'abord en mode **test (sandbox)** de l'opérateur, puis on passe au réel.
