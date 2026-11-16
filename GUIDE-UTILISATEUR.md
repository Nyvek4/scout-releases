# Scout 2.0.0-rc.3 — guide rapide sur Mac

Scout propose **The CIRCLE** (conversation, inscription et jeu sur une borne externe) et **Animation prompts IA**
(35 cartes à QR code). La régie sert à piloter l’animation ; l’écran public est destiné aux visiteurs.

Le paquet corrigé du 16 novembre porte la révision **53fdbf9**. Il réunit le réveil correct du robot dans The CIRCLE, l’aperçu caméra avec aide au scan, les transcriptions vides sans fausse alerte et les sons coupés par défaut avec mémorisation du choix.

## Installer et préparer

1. Téléchargez l’archive **macOS arm64** remise pour cette version et comparez son SHA-256 au fichier fourni.
   Quittez la version précédente, dézippez l’archive puis copiez `Scout.app` dans **Applications**.
   Vos réglages et vos clés sont conservés. Consultez les notes de version jointes au téléchargement.
2. Branchez le robot et son alimentation, dégagez l’espace autour de la tête. Gardez **Reachy Mini Control fermé** :
   Scout gère son propre pilote et peut adopter un pilote déjà présent.
3. Ouvrez Scout. Au premier démarrage, l’installation du pilote peut demander Internet et plusieurs minutes.
   Le démarrage de l’app ne doit pas provoquer de mouvement ; vérifiez les voyants et le bandeau de la régie.
4. Ouvrez **Réglages › Clés**. Saisissez vous-même les clés OpenAI et ElevenLabs, puis **Enregistrer** et **Vérifier**.
   Pour le jeu réel, ajoutez aussi la clé The CIRCLE et son adresse API fournie par l’équipe.
   Les clés sont conservées dans le trousseau et ne sont pas réaffichées : ne les mettez ni dans un chat, ni dans une
   capture, ni dans une adresse de borne. Après une modification de clé, arrêtez puis redémarrez la voix si nécessaire.
5. Dans **Réglages › Périphériques**, choisissez le micro et la sortie **Reachy Mini Audio**. Les boutons de test
   utilisent réellement les périphériques : lancez-les vous-même quand vous êtes prêt. Accordez les permissions
   Caméra et Micro demandées par macOS.
6. Choisissez le contexte voulu dans la régie. Ce choix peut démarrer l’animation ; si le bandeau la signale arrêtée,
   utilisez **Démarrer l’animation**. Ouvrez l’écran public depuis le panneau **Écrans** si nécessaire.

Le paquet macOS de cette version est signé par thecamp et notarisé par Apple. Si macOS signale une archive
endommagée ou une signature invalide, retéléchargez-la et vérifiez son empreinte ; ne désactivez pas Gatekeeper.

## The CIRCLE : un visiteur à la fois

- Sélectionnez **The CIRCLE**, puis **FR** ou **EN** dans la régie. Scout présente le programme ; le QR d’inscription
  permet au visiteur de s’inscrire sur son téléphone. Scout ne collecte pas son prénom.
- Pour jouer, le membre présente le QR de son badge à la caméra ou à la douchette. Scout vérifie le badge puis
  demande le tirage. **La fleur tourne sur une borne externe : aucune roue n’est dessinée dans Scout.**
- Scout attend la révélation de la borne avant d’afficher et d’annoncer le lot reçu. Un son de révélation peut
  accompagner le résultat si les sons sont activés dans la régie. Un refus n’affiche pas de lot.
- Pendant vérification, tirage et verrou de la borne, les autres badges sont ignorés pour préserver le joueur en cours.
  Après expiration, représentez le badge du visiteur suivant. Pour abandonner volontairement le parcours,
  utilisez **Nouveau visiteur** : une réponse tardive ne sera pas attribuée au suivant ; un tirage déjà effectué
  sur la borne n’est pas annulé.
- **Démonstration / simulation / essai** sont signalés à l’écran. Ils ne prouvent pas un gain réel.
- L’adresse facultative **Borne de jeu** dans le panneau The CIRCLE sert de repère opérateur. Scout n’ouvre pas cette
  page et ne la connecte pas à votre place. N’y ajoutez aucun jeton ou mot de passe ; la borne se prépare séparément.

## Scanner un badge avec l’aperçu caméra

Dans **Mode salon**, le panneau **Scanner un badge The CIRCLE** affiche la caméra du robot. Il est aussi disponible dans le panneau Caméra de la régie.

1. Démarrez l’animation, puis présentez le QR entier devant la caméra. Commencez à environ 20–40 cm et ajustez avec l’aperçu. Gardez le QR immobile, sans reflet.
2. **Aider au scan · 16°** lance une recherche lente gauche/droite de 30 secondes maximum. Le mouvement reste dans ±8° et se fige dès qu’un QR est repéré. La voix reste disponible. STOP/PANIC restent prioritaires ; un réarmement ne relance pas la recherche.
3. **Tester sans tirage** vérifie seulement que la caméra lit le badge et reconnaît son format. Aucun appel au jeu, aucun lot. Ce mode reste verrouillé après la lecture et après la fin du panoramique.
4. Le panneau indique **QR repéré**, **badge lu** ou **format non reconnu**. « Format reconnu » ne prouve pas que l’adhésion est valide : seule la vérification du jeu réel le fait.
5. Pour revenir au jeu, retirez d’abord le badge puis cliquez **Terminer l’aide / le test**. Présentez ensuite le badge pour le parcours réel. La roue doit être configurée séparément.

L’aperçu reste local à la régie ; Scout ne l’affiche pas sur l’écran public et n’enregistre pas les images.

## Voix, sons et robot 3D

Les sons d’interface sont coupés par défaut. La case **Sons actifs** dans les réglages du stand permet de les activer ou de les couper ; ce choix est conservé après fermeture et réouverture. Cela ne coupe pas la parole de Scout. Une transcription vide (bruit sans parole reconnue) revient à l’écoute sans alerte de panne ni phrase sonore. Une vraie erreur réseau, de clé ou de budget reste signalée.

Le mode salon propose **Standard** (réglage de départ) et **VAD équilibré** (à l’essai) pour l’interruption de la voix.
Essayez VAD équilibré dans les conditions du stand ; revenez à Standard si le comportement ne convient pas.
Ces réglages ne garantissent pas que toute interruption sera comprise dans le bruit. Les voyants de connexion de la
voix aident à distinguer un problème de réseau, de clé ou de quota. En cas de panne, continuez avec les écrans et la régie.

Sur les écrans d’attente et de conversation The CIRCLE, le robot 3D suit l’état de la voix. C’est une représentation
visuelle : il ne commande pas les moteurs. Une image fixe le remplace automatiquement si le mouvement réduit est
activé, si le rendu graphique est indisponible ou trop lent. Ce repli est prévu ; il n’indique pas une panne du robot réel.

## Animation prompts IA

Présentez une des 35 cartes : sa fiche s’affiche. En cas de QR illisible, utilisez **Forcer une fiche** dans le panneau
du contexte. **Lancer la vidéo / Masquer la vidéo** pilote la vidéo de la fiche ; elle est muette et peut nécessiter
Internet. Une douchette USB peut lire les QR quand la régie a le focus.

## STOP, PANIC et arrêt

| Action | Effet et reprise |
| --- | --- |
| **STOP** ou **Espace** dans la régie, hors champ de saisie | Demande l’arrêt prioritaire des mouvements et de la voix ; les scans sont bloqués. Vérifiez la confirmation avant de réarmer. |
| **PANIC** ou **Échap** | Demande l’arrêt et la veille, puis gèle le contexte. Après vérification de la zone : **Réarmer**, puis **Démarrer l’animation** pour reprendre. |
| **Réarmer** | Lève le verrou de sûreté ; ne doit pas réveiller ni faire bouger le robot à lui seul. |
| **Mettre en veille** | Arrête l’animation. Quittez ensuite Scout avec **Cmd-Q** et attendez l’arrêt du pilote avant de débrancher. |

Une alerte d’arrêt ou de veille **non confirmé** signifie qu’il faut surveiller le robot et libérer la zone ; ne supposez
pas qu’il est arrêté. Si la sûreté impose de couper le mouvement, coupez son alimentation. N’essayez pas de résoudre
un problème de pilote en lançant un second pilote en parallèle.

En cas de souci : vérifiez les voyants, les permissions macOS et les branchements. Dans **Réglages › À propos**,
relevez la version et le SHA, puis utilisez les chemins de journaux indiqués pour le diagnostic avec votre support. Vérifiez
leur contenu avant de les partager ; n’envoyez aucune clé.


## Dépannage rapide

- **OpenAI « Refusée » / erreur 401** : la clé enregistrée est refusée par le service. Saisissez une clé valide,
  enregistrez puis vérifiez-la. Relancez ensuite la voix. Le voyant du micro peut être bon malgré ce blocage.
- **Caméra détectée mais aucune image** : mettez Scout en veille, quittez-le complètement avec Cmd-Q, attendez
  l’arrêt du pilote, puis relancez Scout. Vérifiez la caméra avec le bouton de test avant de reprendre. Si le
  défaut persiste, utilisez une douchette ou la sélection manuelle de fiche pour la démonstration.
- **Pas de voix** : vérifiez séparément OpenAI, ElevenLabs, le micro et la sortie audio dans Réglages.
  Un test micro réussi ne valide pas les services de transcription ou de synthèse.

Cette rc.3 reste une préversion : les essais automatisés ne remplacent pas une répétition complète avec le robot,
les clés et la borne du lieu de démonstration.
