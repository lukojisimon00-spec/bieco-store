# Plan Bieco Store

## Fait
- Site statique (index.html + images/) en ligne : https://bieco-store.vercel.app
- Dépôt GitHub `lukojisimon00-spec/bieco-store`, branche `main`, déploiement automatique Vercel.

## Prochaine étape : paiement Mobile Money avec SasPay
Fournisseur choisi par le propriétaire : SasPay (https://app.saspay.me, doc : https://docs.saspay.me).

À faire, dans cet ordre :
1. Lire la documentation officielle (docs.saspay.me, llms-full.txt, api-reference/openapi.json).
   Vérifier que la RDC est prise en charge (M-Pesa, Orange Money, Airtel Money ; CDF et USD).
   Ne rien supposer qui n'est pas écrit dans la doc.
2. Créer des fonctions Vercel dans `api/` :
   - créer un paiement (clé secrète lue dans `process.env.SASPAY_SECRET_KEY`, jamais dans le HTML) ;
   - recevoir la confirmation (webhook) et vérifier sa signature / vérifier le statut via l'API ;
   - le prix est recalculé côté serveur à partir du catalogue, jamais repris du navigateur.
3. Tester d'abord avec la clé de test (`sk_test_…`) uniquement.
4. Passer en réel seulement avec l'accord explicite du propriétaire.

Règles : jamais de code PIN, OTP ou numéro de carte saisi sur le site ;
une commande n'est « payée » qu'après confirmation de SasPay côté serveur.
