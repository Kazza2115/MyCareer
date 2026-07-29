# 01 — Concept & Vision

## Le pitch

> Tu as 15 ans. Un recruteur t'a repéré au tournoi de quartier. Ce qui se passe ensuite
> ne dépend que de toi — et un peu du destin.

MyCareer est une **simulation de carrière de footballeur pilotée par les choix**. Le joueur
crée un personnage et vit sa carrière saison par saison, de la pré-formation à la retraite,
à travers des décisions textuelles dont les conséquences sont calculées par un moteur
statistique profond. Le jeu se joue dans le navigateur, sur mobile comme sur ordinateur,
sans téléchargement.

La promesse : **aucune carrière ne se ressemble**, et pourtant tout est cohérent — chaque
gloire et chaque échec s'explique par tes choix, tes stats et un peu de chance.

## Les 5 piliers de design

### 1. Chaque choix a un coût
Il n'y a jamais de "bon" choix évident. Signer au grand club, c'est du prestige mais un banc ;
rester au petit club, c'est du temps de jeu mais un plafond. Sortir en boîte améliore ton moral
et tes relations, mais dégrade ta condition. Le jeu doit constamment poser des **dilemmes**,
pas des quiz.

### 2. La profondeur est dans les stats, pas dans le texte
Le texte raconte, mais **tout est simulé**. Une note de match, une offre de transfert, une
blessure, une convocation en sélection : tout découle de formules alimentées par ~30 attributs
visibles, ~10 stats cachées et des états dynamiques (forme, moral, réputation). Le joueur qui
veut optimiser a des années de systèmes à comprendre ; le joueur casual vit juste une histoire.

### 3. L'irréversible crée l'émotion
Une seule sauvegarde par carrière, pas de retour en arrière. Une rupture des croisés à 22 ans,
ça se gère, ça ne s'annule pas. C'est cette tension qui rend un choix mémorable et qui donne
envie de relancer une carrière "pour faire mieux".

### 4. Le monde existe sans toi
Les autres joueurs du monde (générés) vieillissent, progressent, se transfèrent, gagnent des
Ballons d'Or. Tes rivaux de génération sont réels dans la simulation : tu peux passer ta
carrière dans l'ombre d'un phénomène — ou être ce phénomène.

### 5. Chaque carrière enrichit la suivante
Une carrière terminée n'est pas perdue : elle rapporte de l'héritage (méta-monnaie), des
badges, des points de départ débloqués, et entre au Panthéon personnel. La vraie boucle
du jeu n'est pas une carrière — c'est **la collection de légendes** que tu construis.

## Le déroulé d'une carrière

```
Création (15 ans)          Formation (15-18)         Pro (18-~35)              Fin (35+)
─────────────────          ────────────────          ────────────              ────────
Nationalité                Centre de formation       Transferts, titres        Reconversion de poste
Poste & profil de jeu      ou club amateur           Sélection nationale       Dernier défi (exotique?)
Origine sociale            Études vs foot            Blessures, rivalités      Jubilé, retraite
Entourage                  Premier contrat           Vie privée, sponsors      Après-carrière (V2) :
Trait de caractère         Prêts, D2, percée         Prime → déclin            coach, agent, président
```

Chaque saison est découpée en **segments** (pré-saison, automne, hiver/mercato, printemps,
fin de saison, été/mercato) : à chaque segment, le joueur reçoit 1 à 3 événements à choix,
les matchs du segment sont simulés, et les stats évoluent. Une saison se joue en ~5-10 minutes,
une carrière complète en 2-4 heures — mais peut se vivre en dizaines de courtes sessions.

## Différenciation vs Destiny Eleven

| Axe | Destiny Eleven | MyCareer |
|---|---|---|
| Statistiques | Simples, visibles | ~30 attributs + stats cachées + états dynamiques, formules transparentes pour les optimiseurs |
| Matchs | Résumés par saison | Matchs clés joués **minute par minute** avec décisions in-game |
| Monde | Décor narratif | **Monde persistant simulé** : rivaux, Ballon d'Or, palmarès des clubs |
| Relations | Ponctuelles | **Persistantes sur des années** : coach, agent, coéquipiers, famille, rivaux |
| Fin de carrière | Retraite = fin | **Reconversion de poste** en fin de carrière, puis après-carrière (coach/agent) |
| Hors terrain | Basique | Sponsors, médias, réseaux sociaux, investissements, scandales |
| Multijoueur | Défi du jour, versus ami | + Ligues entre amis dans le même univers simulé, carrières duo |
| Méta-progression | 2 perks équipables | Héritage multi-axes : perks, origines débloquées, dynasties (ton fils hérite de traits) |

## Ton et habillage

- **Ton** : réaliste et incarné, avec une pointe d'humour football (surnoms de presse,
  unes de journaux générées, notes de match commentées).
- **Univers** : clubs et joueurs fictifs mais crédibles (ligues inspirées des vraies :
  divisions française, anglaise, espagnole… avec noms détournés), pour éviter tout problème
  de licence et permettre au monde simulé de vivre librement.
- **UI** : mobile-first, sobre, lisible d'une main. La carte de joueur (style carte FUT,
  mais identité propre) est l'objet central que le joueur voit évoluer — et partage.

## Modèle économique (principe)

Gratuit, sans publicité intrusive, sans pay-to-win. Monétisation V1+ : cosmétiques
(cartes, thèmes, maillots), soutien au projet. L'addiction doit venir du jeu, pas de
mécaniques prédatrices — pas de timers payants, pas de loot boxes payantes.
