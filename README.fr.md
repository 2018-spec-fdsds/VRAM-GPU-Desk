# VRAM GPU Desk

[English](README.md) · [Русский](README.ru.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Italiano](README.it.md) · [中文](README.zh.md) · [한국어](README.ko.md) · [日本語](README.ja.md) · [العربية](README.ar.md) · [हिन्दी](README.hi.md) · [Tiếng Việt](README.vi.md)

**Surveillance locale de mémoire GPU et régulation thermique pour Windows x64.**

Version **1.10** · [Installation Windows](downloads/VRAM-GPU-Desk-1.10-Setup-x64.exe) · [ZIP d’installation](downloads/VRAM-GPU-Desk-1.10-Installer.zip)

![VRAM GPU Desk — thème système](images/dashboard-system.png)

## Fonctions

- Affiche VRAM physique utilisée/libre, charge GPU et température avec de petits graphiques historiques.
- Liste les applications et services locaux utilisant la mémoire GPU, avec recherche, tri et filtre facultatif **au-delà de 0,5 GiB**.
- Affiche les dix principales applications et « Autres » en parts normalisées des relevés de mémoire des processus observés pendant les 30 derniers jours. Le total vaut 100 % ; c’est une répartition historique des relevés, pas une décomposition additive de la VRAM physique.
- Indique la proportion du temps d’observation valide des dernières 24 heures où la VRAM physique dépasse 50 %. Les interruptions de surveillance sont exclues.
- Exporte un rapport CSV UTF-8 vers un emplacement local choisi.
- Se réduit dans la zone de notification, restaure la fenêtre existante au lancement suivant et propose le démarrage facultatif avec Windows.
- Offre thèmes système et graphite sombre, douze langues et rafraîchissement de 1 à 5 secondes, 2 secondes par défaut.
- Régulation thermique douce facultative par les limites de puissance et de fréquence prises en charge. La protection est indépendante du rafraîchissement de l’interface.
- Refroidissement au repos, régimes des ventilateurs et icônes animées. Les nouveaux réglages demandent régulation et refroidissement au repos activés ; un arrêt manuel enregistré est conservé. La régulation active n’est affichée qu’après connexion confirmée.
- Alerte après au moins dix secondes strictement au-dessus du seuil choisi de 75–92 °C. Les pointes brèves ne déclenchent pas d’alerte.
- Option d’urgence distincte, initialement désactivée, pour l’application explicitement choisie. Fermer/terminer peut perdre le travail non enregistré ; les processus protégés ou invérifiables sont exclus.

![VRAM GPU Desk — thème graphite](images/dashboard-graphite.png)

## Quatre boutons d’action rapide

Attribuez **Fermer l’application** ou **Terminer le processus** à l’un des quatre boutons et modifiez l’attribution avec le menu `⋮` voisin. Chaque liaison vise l’instance explicitement choisie : PID, date de création et chemin de l’exécutable. À sa disparition, aucun autre processus ni PID réutilisé n’est sélectionné automatiquement.

Le bouton configuré agit d’un clic **sans confirmation supplémentaire**. Le travail non enregistré peut être perdu. Les contrôles natifs des processus protégés, critiques ou invérifiables restent actifs. L’option d’urgence distincte est initialement désactivée et conserve son comportement sur l’application sélectionnée.

## Températures cibles et hystérésis

Des seuils d’arrêt/reprise distincts et de courts délais évitent les basculements fréquents lorsque les valeurs fluctuent.

| Paramètre | Comportement réel | Raison |
|---|---|---|
| Cible au repos, **32 °C** par défaut, réglable 28–40 °C | Après trois secondes à 32 °C ou moins au repos, retour au mode AUTO du micrologiciel. Reprise à 36 °C, soit cible +4 °C. Avec une cible de 35 °C : reprise à 39 °C. | L’hystérésis de 4 °C évite les démarrages/arrêts répétés. Le micrologiciel AUTO décide de l’arrêt complet des ventilateurs. |
| Repos/charge | Jusqu’à 10 % de charge GPU, repos permis ; à partir de 15 %, courbe de charge. Entre 11 et 14 %, état précédent conservé. Charge inconnue : refroidissement maintenu. | Évite les basculements sur de petites variations. |
| Cible thermique douce, 70–88 °C | Puissance et fréquence sont ajustées progressivement selon la tendance thermique. La température peut être inférieure ou dépasser brièvement la cible. | Inertie, capteurs et pilote empêchent un plafond exact. C’est une cible de régulation, pas une coupure d’urgence. |
| Alerte de surchauffe | Relevé strictement supérieur au seuil pendant au moins dix secondes. | Écarte les pointes brèves. |

La température au repos **n’est pas** la limite en charge soutenue. Ambiance, micrologiciel et pilote influencent températures et ventilateurs. N’utilisez pas simultanément des régulateurs de ventilateur/fréquence concurrents sur la même carte.

## Matériel et prérequis

Pour NVIDIA GeForce **RTX 5000 Series**. Mesures et commandes dépendent du GPU et du pilote ; les commandes non prises en charge restent indisponibles, sans simulation.

Windows 10/11 x64, .NET Framework 4.8 et pilote NVIDIA compatible. Le runtime Java est inclus, sans installation séparée. L’utilisateur Windows connecté doit être administrateur avec un jeton de bureau filtré normal. L’installation demande UAC une fois et utilise un répertoire Program Files fixe et protégé. Les identifiants d’un autre administrateur ne sont pas pris en charge. Deux tâches protégées, uniquement à la demande, utilisent des lanceurs fixes et une communication locale typée. Le canal installé vise un démarrage sans nouvelle demande UAC ; si l’authentification échoue, la régulation reste indisponible sans autre élévation.

Pas de liste d’autorisation limitant versions de pilote ou empreintes DLL. NVML système doit réussir la vérification hors ligne de signature Windows avec signataire NVIDIA Corporation confirmé, chemins sûrs et API requises. Un nouveau pilote ne nécessite pas d’ajouter version/empreinte. L’absence de données de confiance locales peut empêcher la vérification ; l’application ne télécharge ni certificats ni pilotes.

## Installation et confidentialité

1. Téléchargez l’installateur et comparez SHA-256 à [SHA256SUMS.txt](SHA256SUMS.txt).
2. Quittez l’ancienne copie par son menu de notification. Lancez normalement depuis le compte administrateur connecté et acceptez UAC. Le dossier protégé est fixe.
3. Ouvrez le nouveau raccourci, choisissez le GPU et vérifiez le statut confirmé du contrôle. Réglez commandes et boutons. Les réglages sont locaux ; les désactivations enregistrées restent désactivées.

L’application utilise les interfaces locales Windows/GPU. Aucun envoi de télémétrie, inférence cloud, mise à jour automatique ou téléchargement de modèle à l’exécution n’est prévu. CSV, historique et réglages restent locaux. Cela **ne garantit pas** l’isolation réseau du système ni le comportement des pilotes tiers, diagnostics Windows ou logiciels de synchronisation.

L’installateur n’est pas signé. L’application est distribuée en binaires compilés ; **son code source n’est pas publié dans ce dépôt**. Le bytecode Java n’est pas chiffré et sa résistance à la décompilation n’est pas garantie. Les notices de licence du runtime tiers sont conservées.

Les captures utilisent des données synthétiques et un état de régulation simulé. Elles illustrent l’interface sans démontrer fonctionnement ou performances matérielles.

## Nouveautés de 1.10

- Quatre boutons configurables liés à une instance pour fermer/terminer d’un clic, réattribuables avec contrôles natifs conservés.
- Descriptions réduites, mini-graphiques de 35 à 55 pixels ; icône de notification contrastée conservée.
- Installation unique du composant protégé avec UAC. Nouveaux réglages thermiques/repos activés ; arrêts manuels enregistrés conservés.
- Correction prudente des alias : exclusion des alias confirmés d’affichage indirect sans rendu, sans fusionner des GPU physiques distincts par nom ou mémoire.
- Réparation des installations incomplètes sûres et indication précise de phase, code et HRESULT si le composant échoue.
- Conservation des thèmes, douze langues, historique local, CSV UTF-8, identité GPU et politiques de bail, surveillance et restauration.

Vérifié : 48 cas d’interface isolés dans douze langues et deux thèmes, icônes, valeurs initiales, liaisons/exécution des actions rapides, contrôles réels de jetons CLR, chemins Unicode, les 163 fichiers et empreintes des brokers intégrées, installation/désinstallation isolée et véritable enregistrement élevé de tâches temporaires avec relecture XML/DACL, annulation et nettoyage. Les tâches **n’ont pas été exécutées** ; aucune modification GPU ni tâche de production n’a été appelée par le test.

Ce test n’a pas exécuté le parcours complet de l’installateur de production ni la commande GPU ultérieure sans UAC. Ces vérifications ne prouvent pas les performances thermiques sous charge soutenue. Les captures sont synthétiques avec régulation simulée.
