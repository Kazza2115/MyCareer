# 05 — Imprévisibilité : ne jamais savoir quelle carrière on va vivre

**Le facteur clé du jeu.** Au moment où il clique sur "Commencer la carrière", le joueur ne
doit **jamais** pouvoir prédire ce qu'il va vivre — ni au 1er essai, ni au 50e. C'est la
promesse du titre : *personne ne connaît son destin à l'avance.*

Le danger à combattre : le **jeu résolu**. Dans la plupart des jeux de carrière, après
10-15 essais, le joueur connaît les événements, connaît les bonnes réponses, et déroule.
La surprise meurt, le jeu aussi. Ce document liste les systèmes qui rendent ça impossible.

Principe directeur : **la surprise doit être structurelle, pas cosmétique**. Changer le nom
du club ou la formulation du texte ne suffit pas — c'est la *trajectoire* de la carrière qui
doit être imprévisible.

---

## 1. Le monde est retiré à chaque carrière

Chaque nouvelle carrière génère un **univers différent** (seed) :

- **La hiérarchie des clubs varie** : le géant de l'univers A est un club en crise dans
  l'univers B. Le club qui te recrute à 16 ans peut être un futur champion d'Europe ou un
  futur relégué — impossible à savoir au moment de signer.
- **L'époque varie** : chaque univers tire une "ère du football" qui pèse sur toute la
  carrière — inflation folle du mercato, ère des milieux créatifs (ton poste vaut plus ou
  moins cher), pays émergent qui achète tout, réforme des compétitions…
- **Ta génération varie** : le nombre et la force des rivaux de ta génération sont tirés au
  sort. Parfois tu es le seul crack de ton âge ; parfois tu grandis dans une génération
  dorée qui t'éclipse — ou que tu peux dominer.

→ Même un joueur qui ferait *exactement les mêmes choix* qu'à sa carrière précédente
vivrait une carrière différente.

## 2. Ton propre joueur est une inconnue

- **Les stats cachées ne sont jamais chiffrées** (cf. doc 02 §2) : tu découvres ta
  fragilité, ton ego, ta mentalité de grand match *en les vivant*. Deux départs identiques
  sur le papier cachent deux joueurs très différents.
- **Le potentiel est dynamique ET invisible** : il bouge selon les événements, et personne
  — pas même toi — n'en connaît la valeur exacte. L'espoir moyen qui explose à 24 ans et le
  prodige qui plafonne existent tous les deux, comme dans le vrai football.
- **Le tirage de création est voilé** : l'origine et l'entourage donnent des *tendances*
  ("ton oncle a joué en D2", "quartier réputé dur"), jamais des chiffres. On choisit une
  histoire, pas un build.

## 3. Les cygnes noirs : événements rarissimes

Une couche d'événements à très faible probabilité (1 carrière sur 20, 50, 100…) qui
**changent tout** quand ils tombent :

| Exemple | Rareté | Effet |
|---|---|---|
| Ton club fait faillite en pleine saison | ~1/30 | Agent libre à contre-temps, marché hostile |
| Rachat du club par un milliardaire | ~1/25 | Stars qui débarquent, ta place menacée — ou tremplin |
| Génération dorée en sélection | ~1/20 | Trophées accessibles, mais concurrence à ton poste |
| Le sélectionneur te déteste (sans raison) | ~1/30 | Arc long : forcer la porte ou changer de nation |
| Maladie/blessure de carrière à 19 ans | ~1/50 | L'arc du come-back — ou une reconversion précoce |
| Scandale d'époque (match truqué autour de toi) | ~1/50 | Témoigner ou te taire : réputation en jeu |
| Le club de ton cœur vient te chercher à 33 ans | ~1/40 | La fin de carrière rêvée, au rabais |

Règles de design des cygnes noirs :
- Ils ne sont **jamais purement bons ou mauvais** — ils rebattent les cartes.
- Ils ont leurs propres arcs de plusieurs années : en croiser un, c'est vivre une carrière
  qu'on ne reverra pas de sitôt.
- Le pool grandit à chaque mise à jour de contenu — la couche la plus rentable en
  rejouabilité par ligne de JSON écrite.

## 4. Le même choix ne produit jamais le même résultat

L'anti-"soluce". La réponse "optimale" à une question **n'existe pas dans l'absolu** :

```
résultat(choix) = f(choix, stats visibles, stats cachées, état du monde, tirage borné)
```

- Signer au grand club est génial *si* ton adaptabilité (cachée) est bonne et *si* le coach
  (dont le style est tiré par univers) aime ton profil. Les guides en ligne ne pourront
  donner que des probabilités, jamais des certitudes.
- **Les dilemmes sont équilibrés par contre-poids** : chaque option a un coût réel
  (cf. pilier "Chaque choix a un coût"). S'il existe une réponse toujours meilleure,
  c'est un bug de game design, au même titre qu'un crash.
- **L'aléa reste borné** (doc 02 §8) : le hasard fait basculer un moment, les stats
  dominent la saison. La surprise vient de la *combinatoire*, pas du dé pur — le joueur
  doit toujours sentir que ça s'explique, jamais que c'est arbitraire.

## 5. La combinatoire des arcs

La variété ne vient pas de N événements isolés, mais de leurs **croisements** :

- Les événements ont des conditions sur des *combinaisons* (stats cachées × état du monde ×
  historique) : l'arc "rival devenu coéquipier" ne peut exister que si ton rival de
  génération a été transféré dans ton club — le moteur du monde crée des situations que
  personne n'a scriptées.
- Les arcs longs (rivalité, promesse, blessure, famille) s'entrelacent : promettre ta
  fidélité à ton club formateur *puis* voir ton rival y signer *puis* recevoir l'offre du
  géant — chaque carrière tisse une combinaison unique.
- Objectif chiffré : **qu'aucune paire de carrières parmi 50 ne partage plus de ~40 % de
  ses événements** — mesuré en télémétrie dès le MVP (distance entre historiques de
  carrières).

## 6. Garantie de nouveauté ("surprise budget")

Des mécanismes explicites, inspirés des roguelikes, pour que le 50e essai surprenne encore :

1. **Anti-répétition mémorielle** : le jeu retient les événements vus dans tes dernières
   carrières et les pénalise fortement au tirage (cf. doc 02 §5.4).
2. **Au moins une première fois par carrière** : le tirage garantit ≥1 événement que *ce
   joueur* n'a jamais vu, pioché dans les couches rares — tant que le pool le permet, et le
   pool grandit à chaque mise à jour.
3. **Contenu en couches profondes** : certains événements exigent des situations que seuls
   les joueurs expérimentés atteignent (3 Ballons d'Or, carrière 100 % fidèle, retraite à
   40 ans…). On découvre encore du contenu au 50e essai *parce qu'on est devenu meilleur*.
4. **Les origines débloquées changent la donne** (doc 03) : "seconde chance à 24 ans",
   gardien, futsal… ne sont pas des skins — elles ouvrent des pools d'événements et des
   contraintes différents. Le méta-jeu recharge la surprise.
5. **Records du monde vivants** : tes propres légendes précédentes existent dans les
   univers suivants comme joueurs historiques à dépasser — le jeu se peuple de tes fantômes.

## 7. Ce qu'on s'interdit

- **La surprise punitive pure** : un cygne noir peut briser une trajectoire, jamais rendre
  la carrière injouable ou ennuyeuse. Toute catastrophe ouvre un arc intéressant.
- **Le brouillard total** : l'imprévisible ≠ l'illisible. Le joueur doit pouvoir se dire
  *"évidemment, avec mon ego et un vestiaire de stars, ça a explosé"* — comprendre après
  coup, jamais prédire avant.
- **La variance cosmétique** : re-skinner le même arc ne compte pas comme de la nouveauté.
  La télémétrie mesure la variété des *trajectoires* (postes, ligues, trophées, courbes
  d'OVR), pas des textes.

---

## Résumé : les 6 sources d'imprévisibilité

| # | Source | Répond à |
|---|---|---|
| 1 | Monde retiré à chaque carrière (clubs, ère, génération) | "Je connais la carte" |
| 2 | Joueur aux stats cachées et potentiel invisible | "Je connais mon build" |
| 3 | Cygnes noirs rarissimes à arcs longs | "J'ai tout vu" |
| 4 | Résultats dépendants du contexte, dilemmes sans réponse dominante | "Je connais la soluce" |
| 5 | Combinatoire des arcs et du monde simulé | "Je reconnais les scripts" |
| 6 | Garanties de nouveauté + contenu en couches profondes | "Le 50e essai me lasse" |
