# hazim-install — installation guidée chez un client

Plugin Claude de **Hazim Systems**. Une seule commande, **`/installhazim`**, installe l'application PFC chez un
cabinet, avec le client à côté (ou en appel). Claude parle en français simple et dit sur quel bouton cliquer.

L'application doit **déjà être en ligne** (Railway). `/installhazim` fait le reste :

| Étape | Qui |
|---|---|
| 1. Vérifier l'ordinateur (Node.js, Chrome) | Claude |
| 2. Autorisations de Claude (liste précise, pas de « bypass ») | Claude ; le client clique « Autoriser » |
| 3. Ouvrir la fenêtre Chrome de Claude | Claude |
| 4. Se connecter à Google | **Le client** (mot de passe) |
| 5. Projet Google, accès Drive et Gmail | Claude |
| 6. Écran de connexion Google | Claude ; **le client** coche la case d'accord de Google |
| 7. Clé de connexion Google | Claude |
| 8. Coller les clés dans Railway | **Le client** (Claude ne voit jamais la clé secrète) |
| 9. Publier et tester « Se connecter avec Google » | Claude, puis le client se connecte |
| 10. Plugin du cabinet (`pfc-cabinet`) | Claude |
| 11. Contrôle du matin à 8 h | Claude |

Ensuite : `/installation-whatsapp` (QR code WhatsApp), puis Drive et Gmail dans **Agents** de l'application.

## Installer le plugin (une fois par ordinateur)

Dans le **Terminal** (⌘ + Espace, tapez `Terminal`, Entrée), collez chaque ligne puis Entrée :

```
claude plugin marketplace add 6ts4s7twsb-ai/hazim-install
```
```
claude plugin install hazim-install@hazim-install
```

Ouvrez Claude (onglet **Code**) et tapez **`/installhazim`**.

## Pourquoi une liste d'autorisations et pas « bypass permissions »

L'ordinateur d'un cabinet contient les données comptables de ses clients. Le mode « bypass » laisserait Claude tout
faire sans demander. `/installhazim` ajoute seulement ce dont il a besoin (`autorisations/settings-hazim.json`) :
sa fenêtre Chrome, vérifier l'adresse de l'application, installer le plugin du cabinet, écrire dans `~/.hazim`.

## Ce que Claude ne fait jamais

- Taper ou lire un mot de passe, un code SMS ou la clé secrète Google.
- Cocher une case d'accord (conditions de Google, de Railway) à la place du client.
- Payer quoi que ce soit : tout est gratuit.

## Reprendre une installation

La progression est gardée dans `~/.hazim/installation.json`. Retapez `/installhazim` : Claude reprend à l'étape
suivante.
