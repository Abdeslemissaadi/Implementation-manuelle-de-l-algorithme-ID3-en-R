# Implementation-manuelle-de-l-algorithme-ID3-en-R

Ce code calcule l'entropie conditionnelle de la variable cible (Activité : Oui/Non) selon quatre attributs sur un dataset de 9 observations. Cette étape permet de déterminer quel attribut apporte le plus d'information pour constituer le nœud racine d'un arbre de décision.

Formule mathématique appliquée

Pour chaque sous-groupe d'un attribut, le code applique la formule de l'entropie de Shannon :

H(S) = - SUM( p_i * log2(p_i) )

L'entropie conditionnelle globale de l'attribut est ensuite obtenue par la moyenne pondérée de l'entropie de ses sous-groupes :

H(S|A) = SUM( (|S_v| / |S|) * H(S_v) )

Détail des calculs par attribut

Script 1 — Météo (Soleil / Nuages) :

Soleil (5 jours : 2 oui / 3 non) -> H(Soleil) = 0,971

Nuages (4 jours : 1 oui / 3 non) -> H(Nuages) = 0,811

Résultat -> entropie_meteo

Script 2 — Amis présents (Présents / Absents) :

Présents (4 jours : 2 oui / 2 non) -> H(Présents) = 1,000

Absents (5 jours : 1 oui / 4 non) -> H(Absents) = 0,722

Résultat -> entropie_amis

Script 3 — Vent (Fort / Faible) :

Fort (4 jours : 0 oui / 4 non) -> H(Fort) = 0,000 (sous-groupe pur)

Faible (5 jours : 3 oui / 2 non) -> H(Faible) = 0,971

Résultat -> entropie_vent

Script 4 — Jour (Weekend / Semaine) :

Weekend (5 jours : 2 oui / 3 non) -> H(Weekend) = 0,971

Semaine (4 jours : 1 oui / 3 non) -> H(Semaine) = 0,811

Résultat -> entropie_jour

Objectif algorithmique

Ces calculs servent à mesurer le Gain d'Information de chaque variable :

Gain(S, A) = H(S) - H(S|A)

Critère de décision : L'attribut qui possède la plus petite entropie conditionnelle (et donc le plus grand gain d'information) sera choisi comme nœud racine de l'arbre de décision.

Environnement technique

Langage : R
