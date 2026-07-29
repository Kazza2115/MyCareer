# 02 — Système de statistiques

C'est le cœur du jeu. Tout ce qui arrive au joueur — notes de match, offres de transfert,
blessures, unes de presse — découle de ce système. Objectif : **assez profond pour être
optimisé pendant des mois, assez lisible pour qu'un débutant comprenne pourquoi il a raté
sa carrière**.

Le système repose sur 4 couches :

```
┌────────────────────────────────────────────────────────────┐
│ 1. ATTRIBUTS (visibles, 0-99)        ~30, évoluent lentement│
│ 2. STATS CACHÉES (révélées peu à peu) ~10, quasi fixes      │
│ 3. ÉTATS DYNAMIQUES                   forme, moral, fatigue…│
│ 4. RÉPUTATION & MARCHÉ                réputation, valeur, $ │
└────────────────────────────────────────────────────────────┘
```

---

## 1. Attributs visibles (0-99)

### 1.1 Technique
| Attribut | Sert à |
|---|---|
| Finition | Convertir les occasions (dans la surface) |
| Frappe de loin | Buts hors surface |
| Passes courtes | Conservation, note de milieu |
| Passes longues | Renversements, passes décisives des DC/MDC |
| Vision | Passes décisives, occasions créées |
| Dribble | Éliminer, provoquer penaltys/fautes |
| Contrôle | Réduire les pertes de balle, jouer sous pression |
| Centres | Passes décisives des ailiers/latéraux |
| Coups francs | Buts sur CF directs |
| Penaltys | Conversion des penaltys (+ sang-froid) |
| Jeu de tête | Buts et duels aériens |
| Tacles | Récupérations propres, éviter les cartons |
| Marquage | Duels défensifs, note défensive |

### 1.2 Physique
| Attribut | Sert à |
|---|---|
| Vitesse | Duels en profondeur, contres |
| Accélération | Premiers mètres, dribbles réussis |
| Endurance | Tenir 90 min, enchaîner les matchs sans chuter |
| Force | Duels au corps, protection de balle |
| Détente | Duels aériens |
| Agilité | Changements de direction, gardiens |

### 1.3 Mental
| Attribut | Sert à |
|---|---|
| Sang-froid | Occasions décisives, penaltys, fins de match |
| Positionnement | Être au bon endroit (off. et déf.) |
| Décision | Bons choix balle au pied, réduit les erreurs |
| Leadership | Capitanat, bonus vestiaire, reconversion coach |
| Agressivité | Récupérations ET risque de cartons/blessures infligées |
| Concentration | Éviter l'erreur qui coûte un but (surtout DC/GB) |

### 1.4 Gardien (remplace la technique de champ)
Réflexes, Plongeon, Sorties aériennes, Un-contre-un, Jeu au pied, Placement.

### 1.5 Note globale (OVR)

L'OVR est une moyenne pondérée **par poste**. Exemples de pondérations :

| Attribut | BU | AD/AG | MO | MC | MDC | DC | LAT | GB |
|---|---|---|---|---|---|---|---|---|
| Finition | 25% | 15% | 12% | 5% | — | — | — | — |
| Vitesse+Accél. | 15% | 20% | 8% | 5% | 5% | 8% | 15% | — |
| Dribble+Contrôle | 12% | 20% | 15% | 10% | 5% | — | 8% | — |
| Passes+Vision | 8% | 12% | 25% | 25% | 15% | 8% | 12% | — |
| Tacles+Marquage | — | — | — | 8% | 25% | 30% | 20% | — |
| Mental (mix) | 15% | 10% | 15% | 20% | 20% | 22% | 15% | 20% |
| Physique (mix) | 15% | 13% | 10% | 15% | 20% | 22% | 20% | 10% |
| Jeu de tête | 10% | — | — | — | 5% | 10% | — | — |
| Attributs GB | — | — | — | — | — | — | — | 70% |

**Conséquence de design** : changer de poste change l'OVR. Un ailier de 33 ans qui a perdu
sa vitesse peut redevenir un bon milieu si sa vision et ses passes ont mûri → la
**reconversion de poste** est une vraie mécanique de fin de carrière.

### 1.6 Échelle de lecture

| OVR | Niveau |
|---|---|
| 40-54 | Amateur / réserve |
| 55-64 | Pro de division inférieure |
| 65-74 | Titulaire de première division moyenne |
| 75-84 | International, club de haut de tableau |
| 85-92 | Classe mondiale |
| 93-99 | Légende historique (quelques joueurs par génération) |

---

## 2. Stats cachées

Fixées majoritairement à la création (influencées par l'origine, l'entourage, le trait de
caractère choisi), **révélées progressivement** par les événements — un des plaisirs du jeu
est de découvrir qui est vraiment ton joueur.

| Stat cachée | Effet | Révélée par |
|---|---|---|
| **Potentiel (PA)** | Plafond de progression… mais **dynamique** (voir 3.4) | Rapports de recruteurs, comparaisons presse |
| **Professionnalisme** | Vitesse de progression, résistance au déclin, gestion des tentations | Événements de vie (soirées, entraînements) |
| **Ambition** | Réactions au banc, exigences de transfert ; ambition + patience = carrière longue au top | Négociations, interviews |
| **Loyauté** | Bonus moral en restant, malus réputation en trahissant | Offres de rivaux |
| **Ego** | Conflits vestiaire/coach, mais bonus "grand match" si flatté | Conférences de presse, hiérarchie |
| **Fragilité** | Probabilité de blessure (voir 5.3) | Historique de blessures |
| **Récupération** | Vitesse de retour de blessure et de fatigue | Retours de blessure |
| **Consistance** | Variance des notes de match (élevée = régulier) | Sur une saison de notes |
| **Grands matchs** | Bonus/malus de perf dans les finales, derbys, barrages | Les finales, justement |
| **Adaptabilité** | Vitesse d'intégration à l'étranger (langue, culture) | Transferts à l'étranger |

**Règle d'or** : les stats cachées ne sont jamais affichées en chiffres. Elles transparaissent
dans les textes ("Ton agent te trouve un peu trop gourmand", "Le staff médical s'inquiète de
tes ischios"). Les joueurs avancés apprendront à les diagnostiquer — profondeur gratuite.

---

## 3. Progression des attributs

### 3.1 Sources d'XP

Chaque saison (une année = 2-3 décisions du joueur, le reste est simulé), le joueur gagne de l'XP :

```
XP_saison = XP_matchs + XP_entraînement + XP_événements

XP_matchs      = Σ sur les matchs joués :
                 base(minutes) × facteur_note × importance × mult_âge
  base          : 90 min = 10 XP, remplaçant 20 min = 3 XP, tribune = 0
  facteur_note  : note 5.0 → ×0.6 · note 7.0 → ×1.0 · note 9.5 → ×1.6
  importance    : amical ×0.5 · championnat ×1.0 · coupe ×1.2 ·
                  continental ×1.5 · sélection ×1.4 · finale ×1.8
  mult_âge      : 15-18 ans ×1.5 · 19-23 ×1.2 · 24-28 ×1.0 · 29+ ×0.6

XP_entraînement = qualité_infrastructures(club) × qualité_coach
                  × (professionnalisme/100 + 0.5) × focus
XP_événements   = bonus/malus narratifs (stage d'été, mentor, etc.)
```

**Le dilemme central du jeu** vit dans cette formule : un titulaire en D2 (12 XP/match ×1.0)
progresse plus vite qu'un remplaçant en Ligue des Champions (3 XP/match ×1.5) — mais le second
a l'entraînement d'élite, la réputation et les opportunités. Aucune réponse n'est toujours bonne.

### 3.2 Répartition de l'XP

- **70 % automatique** : répartie selon le poste et le *style de jeu* choisi à la création
  (ex. "Renard des surfaces" oriente vers finition/positionnement, "Poison des défenses"
  vers vitesse/dribble). Le style peut évoluer via des événements rares.
- **30 % libre** : le joueur place des points d'entraînement à chaque intersaison
  (agency + moment de projection agréable).
- **Rendements décroissants** : passer un attribut de 60→61 coûte peu, de 85→86 coûte ~4×
  plus. Empêche les monstres uniformes, encourage les profils marqués.

### 3.3 Courbe d'âge

Chaque attribut appartient à une famille avec sa propre courbe :

```
Physique   : pic 23-27, déclin rapide dès 29 (vitesse/accél. en premier)
Technique  : pic 26-30, déclin lent
Mental     : croît jusqu'à ~32, ne décline presque pas
Gardien    : pic 28-33
```

Le déclin annuel (appliqué à l'intersaison) :

```
déclin = base_âge × (1.4 − professionnalisme/100) × mult_hygiène_de_vie
         × (1 + blessures_graves_carrière × 0.15)
```

Un joueur pro, sobre et épargné par les blessures joue au top jusqu'à 35 ans. Un talent
fêtard et fracassé décline dès 28. **Le déclin est l'histoire de la fin de jeu** : le vivre
(refuser de vieillir, se reconvertir, partir dans un championnat exotique) doit être aussi
intéressant que l'ascension.

### 3.4 Potentiel dynamique

Contrairement aux jeux de gestion classiques, le PA n'est **pas une constante** :

- PA initial tiré à la création (influencé par l'origine : quartier difficile = variance
  haute, académie huppée = variance basse).
- Événements charnières le modifient de ±2 à ±5 : mentor légendaire, blessure grave à 17 ans,
  saison blanche, déclic psychologique…
- Le PA **effectif** ne peut jamais être connu exactement — les recruteurs du jeu donnent
  des fourchettes ("il peut viser la Ligue 1… voire mieux").

Design : ça élimine le réflexe "je restart si mon PA est mauvais", puisque le PA se joue
aussi. Une carrière moyenne peut basculer.

---

## 4. États dynamiques (le court terme)

Ces états fluctuent **à l'intérieur de la simulation de saison** (le moteur joue chaque
match en interne) ; le joueur en voit l'état au moment de chaque question et dans le bilan
annuel ("saison en dents de scie : gros hiver, printemps en berne après ta blessure").

| État | Échelle | Évolution | Effet |
|---|---|---|---|
| **Forme** | 0-100 | Moyenne mobile pondérée des 5 dernières notes | ±10 % sur toutes les perfs de match |
| **Moral** | 0-100 | Temps de jeu, résultats, vie privée, relations | ±8 % perfs, ±20 % XP |
| **Fatigue** | 0-100 | +par match/voyage, −par repos ; chronique si enchaînement | Perfs, et ×risque de blessure |
| **Rythme** | 0-100 | Chute pendant blessure/tribune, remonte en jouant | Plafonne la note de match |
| **Confiance du coach** | 0-100 | Perfs, événements, attitude | Détermine le temps de jeu de la saison |

La boucle perverse à équilibrer soigneusement : mauvaise passe → moins de confiance coach →
moins de temps de jeu → rythme en berne → pires perfs. Le jeu doit fournir des **portes de
sortie** (prêt, discussion avec le coach, mercato, coupe nationale pour se montrer) pour que
ce soit une spirale *à briser par des choix*, pas un puits sans fond.

---

## 5. Simulation des matchs et des saisons

### 5.1 Note de match

Chaque match simulé produit une note (2-10), l'unité de feedback centrale du jeu :

```
note = 6.0
     + (contribution_poste − niveau_opposition) × 0.8   // ton niveau vs l'adversaire
     + forme_mod + moral_mod + rythme_mod               // états du moment
     + événements_de_match                              // buts +1.0, passe D +0.7,
                                                        // penalty raté −0.8, CSC −1.5,
                                                        // rouge −2.0, clean sheet (déf) +0.5
     + N(0, σ)                                          // aléa, σ réduit par Consistance
     [× bonus_grands_matchs si finale/derby]
```

`contribution_poste` = moyenne pondérée des attributs pertinents du poste (même table que
l'OVR). Les buts/passes sont tirés par des lois de Poisson paramétrées par les attributs
offensifs, le niveau de l'équipe et le temps de jeu — pour qu'en fin de saison, les stats
(buts, passes, clean sheets) soient crédibles pour la ligue et le poste.

### 5.2 Matchs clés joués minute par minute

**Au plus 1 match par saison, et seulement les années charnières** (finale, derby décisif,
barrage) — il compte alors comme l'une des 2-3 questions de l'année. Il se joue en **mode
temps fort** : une séquence courte de 2-4 moments avec décisions :

> 87e minute. 1-1. Penalty pour vous. Le tireur attitré est là, mais le Kop scande ton nom.
> → Prendre le ballon (sang-froid + penaltys testés, gloire ou fardeau)
> → Laisser le tireur (relation +, mais la presse notera ta discrétion)

Ces moments utilisent les mêmes stats que la simulation — un choix courageux avec des stats
faibles reste risqué. C'est là que naissent les moments mémorables qu'on raconte.

### 5.3 Blessures

```
P(blessure) = base_minutes_jouées × fragilité × (1 + fatigue/150)
              × mult_agressivité_adverse × mult_hygiène_de_vie
```

Gravité : 70 % bénigne (quelques semaines), 25 % sérieuse (2-4 mois), 5 % grave (6-12 mois,
−1 à −3 attributs physiques permanents, PA ajusté si jeune). Une blessure grave devient
l'une des questions de l'année ("comment vis-tu ta rééducation ?") et colore le bilan de
saison — jamais juste une ligne "blessé 4 mois".

---

### 5.4 Sélection des 2-3 questions de l'année

À chaque année, le moteur choisit les questions dans le pool d'événements selon un score
de pertinence :

```
score_événement = conditions_remplies (âge, OVR, situation club, états, stats cachées)
                × poids_dramatique   (un mercato chaud > une interview banale)
                × continuité_d'arc   (suite d'un arc ouvert : blessure, rivalité, promesse)
                × anti-répétition    (pénalité si vu dans une carrière récente)
```

Règles de composition d'une année :
- **1 question "trajectoire"** garantie (club, contrat, poste, sélection) ;
- **1 question "vie"** (entourage, argent, vie privée, médias) ;
- la 3e est optionnelle : arc en cours, match clé, ou événement rare.

Les arcs narratifs (rivalité, blessure grave, promesse faite à un club) s'étalent ainsi
sur plusieurs années sans jamais dépasser le budget de questions.

## 6. Réputation, marché et argent

### 6.1 Réputation (3 niveaux)

- **Locale** (ton club, tes fans) : temps de jeu, perfs, gestes envers le club.
- **Nationale** (ta ligue, ta sélection) : stats de saison, trophées, médias.
- **Mondiale** : compétitions continentales, sélection, récompenses individuelles.

La réputation pilote : les offres de transfert reçues, la convocation en sélection,
les sponsors, le vote Ballon d'Or. Elle **retombe lentement** si les perfs s'arrêtent —
et elle survit partiellement à la retraite (base de l'après-carrière).

### 6.2 Valeur marchande & salaire

```
valeur = base(OVR) × mult_âge × mult_potentiel_perçu × mult_forme_saison
         × mult_contrat_restant × mult_réputation
```

Le salaire se **négocie** (événements dédiés, ton agent compte) : salaire élevé = confort et
statut, mais pression du vestiaire et attentes des fans (la presse détruit un joueur payé
comme une star qui joue comme un remplaçant → moral).

### 6.3 L'argent comme ressource de jeu

L'argent gagné se dépense en choix de vie : entourage (meilleur agent, préparateur privé
= bonus concrets), immobilier/investissements (revenus passifs, sécurité post-carrière),
famille, plaisirs (moral vs professionnalisme). En fin de carrière, le patrimoine conditionne
les options d'après-carrière. Faillite possible pour les flambeurs — c'est un arc narratif,
pas un game over.

---

## 7. Le monde simulé

Pour que les stats du joueur aient un sens, le monde doit vivre :

- **~2000 joueurs IA persistants** par univers de carrière : les 30-50 "notables" de ta
  génération (rivaux, coéquipiers stars) sont simulés individuellement (progression, transferts,
  palmarès) ; le reste est simulé statistiquement par club.
- **Clubs** : force d'effectif, prestige, budget, style — évoluent selon leurs résultats simulés.
- **Palmarès du monde** : championnats, coupes, Ballon d'Or attribués chaque saison. Ton nom
  peut y figurer. Tes records peuvent être battus par l'IA des carrières suivantes.
- **Rivaux de génération** : à la création, 2-3 rivaux sont générés (même âge, même poste ou
  presque). La presse vous compare toute votre carrière. Les battre est une source de quêtes
  et de fierté ; l'un d'eux peut devenir ton coéquipier, ton ennemi ou ton ami.

---

## 8. Transparence : le contrat avec le joueur

- Les **attributs et états** sont visibles, avec des flèches d'évolution après chaque saison.
- Les **formules exactes** ne sont pas affichées, mais chaque conséquence est **expliquée**
  ("Note en baisse : tu manques de rythme après ta blessure").
- Les **stats cachées** ne sont jamais chiffrées, seulement suggérées par le texte.
- L'**aléa existe mais est borné** : la chance fait basculer un match, jamais une carrière.
  Sur une saison, les stats dominent toujours le bruit.
