# VRAM GPU Desk 1.21

## Nouveautés 1.21 — alimentation facultative et contraste automatique

**Disposition facultative.** Si la surveillance est désactivée ou si aucune alimentation compatible n’est détectée, sa carte est masquée et les autres utilisent la largeur disponible, sans emplacement vide. Après détection d’une alimentation, sa carte reste visible avec des tirets lorsque les mesures sont temporairement indisponibles.

**Tableau de bord plus compact.** La carte « Temps avec VRAM > 50 % » a été retirée des vues à un et deux GPU. Le classement des applications sur 30 jours et l’historique enregistré sont conservés.

**La surveillance de l’alimentation est désactivée par défaut.** Une case distincte ajoute une carte indiquant la puissance de sortie disponible et les courants de deux connecteurs GPU réels au maximum. Les valeurs absentes ou périmées affichent — ; les courants des rails ne sont pas assimilés à ceux de connecteurs individuels. Le composant protégé de lecture seule s’installe lors de la configuration UAC unique et n’acquiert aucun contrôle GPU.

**La compatibilité dépend du modèle.** La lecture a été vérifiée sur MSI MPG Ai1300TS. Ai1600TS est qualifié par protocole. Certains Corsair HXi/RMi, Thermaltake DPS G/iRGB PLUS et, en complément, NZXT E ont passé des tests synthétiques ; leur validation matérielle reste à faire. Corsair fournit des watts mesurés, le total Thermaltake est explicitement calculé ; NZXT fournit les rails sans inventer de total. be quiet! Dark Power Pro 14 IO a été étudié ; aucun lecteur n’est qualifié pour Seasonic OptiGuard ou ASUS. Aucune prise en charge globale des six marques n’est annoncée. Voir [compatibilité des alimentations](docs/psu-compatibility.md).

**Le contraste automatique du texte est activé par défaut.** Le texte s’adapte au fond ; désactivez cette option pour choisir manuellement un texte clair ou sombre. Transparence, indicateurs compacts, deux superpositions NVIDIA distinctes, double-clic vers la fenêtre, positions et couleurs/sons de température sont conservés.

Les captures graphite utilisent des données synthétiques, alimentation comprise. Les réglages GPU, actions sur les processus, modes d’urgence et choix enregistrés sont conservés.

[Windows x64 EXE](downloads/VRAM-GPU-Desk-1.21-Setup-x64.exe) · [Installer ZIP](downloads/VRAM-GPU-Desk-1.21-Installer.zip)
