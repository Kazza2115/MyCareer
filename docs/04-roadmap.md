# 04 — Roadmap

Principe : sortir vite une boucle de jeu complète et déjà plaisante (MVP), puis empiler
la profondeur par couches. Chaque palier est jouable et testable.

## MVP — "Une carrière complète" 

La boucle 15 ans → retraite, entièrement jouable dans le navigateur, sans compte.

- [ ] Création de joueur : nationalité, poste, origine, entourage, trait, style de jeu
- [ ] Monde généré par seed à chaque carrière : hiérarchie des clubs retirée, ère du
  football, génération de rivaux (le socle de l'imprévisibilité, cf. doc 05)
- [ ] Moteur de stats : ~30 attributs, OVR par poste, stats cachées de base
  (potentiel, professionnalisme, fragilité, consistance)
- [ ] Simulation de saison complète en un tour : notes de match, buts/passes (Poisson),
  classement du club, XP et progression, courbe d'âge et déclin
- [ ] Rythme de jeu : **2-3 questions par année** + bilan de saison condensé
- [ ] Système d'événements data-driven (JSON) : ~120 événements avec conditions et effets
- [ ] États dynamiques : forme, moral, fatigue, confiance du coach
- [ ] Transferts et contrats simples (offres selon OVR/réputation, négo salaire basique)
- [ ] Blessures (3 niveaux de gravité)
- [ ] Sélection nationale (convocations, compétitions majeures)
- [ ] Bilan de saison + Récit de carrière final + score de légende
- [ ] Carrières type : empreinte de carrière + bibliothèque initiale (~40 références
  couvrant tous les postes et tous les étages) + comparaison finale "Ta carrière
  ressemble à…" (doc 06)
- [ ] Sauvegarde locale (localStorage), reprise de partie
- [ ] UI mobile-first, carte de joueur évolutive

**Contenu cible MVP** : 1 univers de ~10 championnats et ~160 clubs fictifs couvrant
déjà les grandes routes mondiales — 5 grands d'Europe, Brasileirão, Argentine, Arabie
saoudite, MLS ou Japon, D2 (détail : doc 07 §5) —, ~120 événements,
carrière jouable en **20-30 minutes** (~40-50 questions du début à la retraite). Le pool
d'événements doit être ~3× plus grand que ce qu'une carrière consomme, pour que deux
carrières d'affilée ne se ressemblent pas.

## V0.2 — "On y revient"

La méta-progression qui donne envie de relancer.

- [ ] Héritage, perks de départ (2 équipables), origines débloquées
- [ ] Badges (~60 au lancement, dont secrets)
- [ ] Panthéon personnel (galerie des carrières)
- [ ] Matchs clés minute par minute (finales, derbys) avec décisions in-game
- [ ] Rivaux de génération (2-3 IA persistantes comparées par la presse)
- [ ] Cygnes noirs : premier lot de ~10 événements rarissimes à arcs longs
- [ ] Bibliothèque de carrières type étendue à ~100 références + collection des
  silhouettes au Panthéon + badges secrets liés (ex. "obtenir Pirlo")
- [ ] Garanties de nouveauté : anti-répétition mémorielle + ≥1 "première fois" par carrière
- [ ] Télémétrie de variété : mesure de la distance entre carrières (objectif doc 05 §5)
- [ ] Équilibrage par simulation de masse : des bots jouent des milliers de carrières pour
  vérifier qu'aucun départ n'est une "graine morte" et que tous les archétypes de légende
  sont viables (doc 05 §7)
- [ ] Carte de carrière partageable (image générée)

## V0.3 — "Le rendez-vous quotidien"

Le backend arrive (comptes optionnels, Supabase ou équivalent).

- [ ] Sauvegarde cloud (compte optionnel — on peut toujours jouer sans)
- [ ] Défi du jour (graine partagée) + classement quotidien + streak
- [ ] Panthéon mondial (classement des scores de légende, global/pays/amis)
- [ ] Défis hebdo à contraintes

## V1.0 — "Le monde vivant"

- [ ] Monde persistant complet : joueurs IA notables simulés individuellement,
  Ballon d'Or, records du monde battables
- [ ] Univers des clubs complet : ~30 championnats, ~600 clubs, toutes confédérations,
  compétitions continentales + mondial des clubs (doc 07)
- [ ] Relations persistantes (coach, agent, coéquipiers, famille) avec historique
- [ ] Vie hors terrain : sponsors, médias/réseaux sociaux, argent et investissements
- [ ] Reconversion de poste en fin de carrière
- [ ] PWA installable, boutique cosmétique, ~300 événements

## V2.0 — "Au-delà du joueur"

- [ ] Après-carrière : entraîneur, agent ou président (avec l'héritage de ta carrière)
- [ ] Dynasties : incarner l'enfant d'une de tes légendes
- [ ] Ligues entre amis dans un univers partagé, carrières duo
- [ ] Mode Histoire : rejouer/dépasser des carrières légendaires prédéfinies

## Stack technique pressentie

- **Frontend** : React + TypeScript (Vite), UI mobile-first, PWA
- **Moteur de jeu** : TypeScript pur, découplé de l'UI (testable, portable, et le défi du
  jour pourra être vérifié côté serveur avec le même code)
- **Contenu** : événements/clubs/noms en JSON versionné — itérer sur le contenu sans build
- **Backend (V0.3+)** : Supabase (auth, Postgres, classements) ou API Node légère
- **Sans compte d'abord** : localStorage ; le compte n'est proposé que quand il apporte
  quelque chose (cloud, classements)
