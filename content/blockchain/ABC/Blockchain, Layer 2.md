tags : #blockchain #on_process 

Explication :
Un layer 2 tout simplement est une blockchain qui viendra contribuer au bon fonctionnement d'une blockchain de layer 1 (ethereum, bitcoin) elle viendra apporter quelqu'un chose de + lui permettant d'être plus performante par exemple.
On retrouve par exemple **Polygon** pour **ethereum** ou bien **Litecoin** pour **bitcoin**.
On sait qu'une blockchain subit le [[blockchain trilemma]]
![](https://i.imgur.com/WvYu54w.png)

Vulgarisation :
dans un setup gamer par exemple on retrouve plusieurs composants mais parlons des écrans, si un utilisateur a 1 écran 24" dans son setup, c'est cool, ça fonctionnera quand même mais pour certaines tâches il sera moins performant, maintenant si on lui met un écran 38 pouces, il poura gérer plus de tâches sur un seul écran et verra sa performance accrue, c'est la même chose pour les layer2, chacune d'entre elles vient rajouter son petit +

### C'est quoi une sidechain ?
- Une sidechain = indépendante et racollée à la blockchain
- a ses propres stats (validateurs, consensus, ect..)
- utilise des bridges pour être relié à la blockchain de layer1
- doit être compatible à la main chain (ex eth = EVM)
- est autonome
- Pas trop un layer2 mais aide la blockchain mère
![](https://i.imgur.com/RdKLedU.png)
- Indépendante (hérite pas de la sec de la main blockchain, doit être construite from scratch)
![](https://i.imgur.com/soRa8HE.png)
### C'est quoi un plasma ?
- Inventé par vitalik butterin
- Ensemble de mini clone de la chain principal donc LAYER 1 qui vont venir se racoller afin de fonctionner ensemble
- Utilise des algo comme l'arbre de merkle ou rollup pour créer une blockchain au dessus d'une infité d'autre blockchain.
- améliore le débit, diminue les frais de txn
- sécurité dépendante de la blockchain principale (presque, même implémentation niveau code mais pas la même infra donc sécurité 95% authentique)
- permettent de transférer des fonds mais n'éxecutent pas de smart contracts

### Les channels
- Se fait en offchain en ouvrant un channel par exemple entre nous et un ami, on se fait les transferts dans ce channel en utilisant la technologique multisig, une fois ce channel fermé la transaction part on-chain et s'inscrit donc sur blockchain
- s'inscrire en utilisant un contrat multi sig ?
- c'était utilisé avant mais plus trop maintenant pcq trop chiant de s'inscrire pour ouvrir un channel, mais l'idée a été reprise par ex par le lightning network de bitcoin qui fonctionne en utilisant ce système de channel bi directionnel
- UN CHANNEL EST BIDIRECTIONNEL
- Raiden, connext, state channel fonctionnent avec ça
![](https://i.imgur.com/kHgct3t.png)
`
### Les plus connus, les roll'up
- Très utilisés dans les blockchain
- Prend plusieurs transactions et les enroule en une seule donnée (souvent block), fonctionne comme un aggrégateur de donnée, évitant ainsi la donnée de traiter 2 fois x txn,y txn mais 1 fois x+y txn, on appelle ça un batch.
- il existe 2 types de rollup, les [[ZK-Rollup]] et les [[Optimistic rollup]]
![](https://i.imgur.com/7gCpHHJ.png)
#### Optimistic rollup :
- La création des batch cités plus haut se fait par un smart contract appelée "agreggator"
- est optimiste, donc considère que l'aggrégateur qui envoie les transactions est honnête et envoie toujours les bonnes informations
- Une fois les info envoyés, pendant 7 jours elles sont mise de côté, si un utilisateur du main net ou rollup envoie une preuve de fraude, et prouve au protocol que quelque chose ne va pas et que l'aggrégateur a envoyé un mauvais batch.
- Si batch invalide, alors on rollback, on punit l'aggrégateur (on le slash) et on lui retire de l'argent pour avoir été malhonnête
- Exemple de rollup optimistic : Optimism
![](https://i.imgur.com/75oYRqC.png)
![](https://i.imgur.com/DCJbAfk.png)

#### ZK rollup :
- Fait confiance à personne parce que : Zero Knowledge technologie (méthode soumettant un issuer et un verifier, le verifier soummet plusieurs challenge cryptographique si l'issuer répond 100% juste c'est qu'il ce qu'il dit est vrai, pour autant les challenges cryptographique ne font divulguer aucune information relié au sujet qui impose la vérification)
- ex de rollup : polygon, zksync, starknet