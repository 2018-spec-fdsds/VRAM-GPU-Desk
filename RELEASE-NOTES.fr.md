# VRAM GPU Desk 1.22

## Nouveautés de la version 1.22 — récupération continue, journal et courants d’alimentation explicites

**Récupération continue du contrôle.** Tant que la récupération forcée est activée, les tentatives vérifiées se poursuivent sans limite de nombre : après 5, 10, 30, puis toutes les 60 secondes. Le dernier choix ACTIVÉ/DÉSACTIVÉ est conservé pendant l’arrêt et le redémarrage du contrôleur. L’avertissement non modal de perte de contrôle se ferme automatiquement uniquement après confirmation par une télémétrie récente. Les vérifications de propriété, d’arrêt complet du client précédent et des limites matérielles restent actives ; cela ne garantit pas un contrôle exclusif face à MSI Afterburner ou à un autre régulateur.

**Journal de l’application.** Un bouton dédié ouvre les événements de perte, récupération et nouvelle tentative par GPU, ainsi que les états initiaux et modifications de toutes les cases liées au contrôle. Chaque entrée comprend les heures UTC et locale. Les températures sont enregistrées à partir de **78 °C**, à chaque changement ultérieur en degrés entiers, puis lors du retour sous 78 °C. La fenêtre affiche jusqu’à 500 événements de la session en cours. Les fichiers UTF-8 restent locaux dans `%LOCALAPPDATA%/VRAMDeskJava/logs/application.log`, avec rotation à 2 MiB et cinq archives.

**Courant maximal d’une broche ou total du connecteur.** Pour chacun des deux ports physiques d’alimentation GPU au maximum, la carte affiche le plus élevé des courants individuels disponibles dès qu’au moins une valeur est connue, même avec des données partielles. Sans lecture individuelle, elle affiche le courant total mesuré du connecteur. Les libellés distinguent explicitement **maximum** et **total**. Les capteurs inconnus restent à — ; un zéro mesuré reste zéro. Les infobulles conservent les valeurs individuelles et le total lorsqu’ils sont disponibles. Le courant d’un rail ne remplace pas une mesure de connecteur.

**Mise à jour d’une ancienne installation 1.9.** Une copie située dans LocalAppData peut continuer de fonctionner alors que 1.22 est correctement installée dans Program Files : l’ancienne interface semble alors dépourvue des nouvelles options. Avant l’installation, quittez l’ancienne copie par son menu de notification ; ensuite, utilisez le raccourci actuel du menu Démarrer et vérifiez **v1.22**. Si un raccourci vise encore l’ancien dossier, ouvrez la copie installée dans Program Files et corrigez le raccourci. Une ancienne fenêtre encore ouverte ne signifie pas que les nouveaux paramètres ont été supprimés.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.22-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.22-Installer.zip)

# VRAM GPU Desk 1.21

## Nouveautés 1.21 — alimentation facultative et contraste automatique

**Disposition facultative.** Si la surveillance est désactivée ou si aucune alimentation compatible n’est détectée, sa carte est masquée et les autres utilisent la largeur disponible, sans emplacement vide. Après détection d’une alimentation, sa carte reste visible avec des tirets lorsque les mesures sont temporairement indisponibles.

**Tableau de bord plus compact.** La carte « Temps avec VRAM > 50 % » a été retirée des vues à un et deux GPU. Le classement des applications sur 30 jours et l’historique enregistré sont conservés.

**La surveillance de l’alimentation est désactivée par défaut.** Une case distincte ajoute une carte indiquant la puissance de sortie disponible et les courants de deux connecteurs GPU réels au maximum. Les valeurs absentes ou périmées affichent — ; les courants des rails ne sont pas assimilés à ceux de connecteurs individuels. Le composant protégé de lecture seule s’installe lors de la configuration UAC unique et n’acquiert aucun contrôle GPU.

**La compatibilité dépend du modèle.** La lecture a été vérifiée sur MSI MPG Ai1300TS. Ai1600TS est qualifié par protocole. Certains Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS et, en complément, NZXT E ont passé des tests synthétiques ; leur validation matérielle reste à faire. Corsair fournit des watts mesurés, le total Thermaltake est explicitement calculé ; NZXT fournit les rails sans inventer de total. be quiet! Dark Power Pro 14 IO a été étudié ; aucun lecteur n’est qualifié pour Seasonic OptiGuard ou ASUS. Aucune prise en charge globale des six marques n’est annoncée. Voir [compatibilité des alimentations](docs/psu-compatibility.md).

**Le contraste automatique du texte est activé par défaut.** Le texte s’adapte au fond ; désactivez cette option pour choisir manuellement un texte clair ou sombre. Transparence, indicateurs compacts, deux superpositions NVIDIA distinctes, double-clic vers la fenêtre, positions et couleurs/sons de température sont conservés.

Les captures graphite utilisent des données synthétiques, alimentation comprise. Les réglages GPU, actions sur les processus, modes d’urgence et choix enregistrés sont conservés.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)
