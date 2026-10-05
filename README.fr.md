# RADAR

Des preuves de gouvernance pour les applications et les agents d'IA. Un produit
d'AKIOUD AI.
[English version](README.md)

RADAR est à la fois la boîte noire et le carnet de bord de l'IA d'une
entreprise. La boîte noire enregistre ce que l'IA a fait ; le carnet de bord
garde ce que les humains ont décidé à son sujet. L'entreprise peut ainsi
répondre, preuves en main, à la question : « que fait votre IA, et qui la
contrôle ? »

Ce dépôt présente le produit. Il ne contient pas de code source.

## Pour qui

Les entreprises qui utilisent des applications d'IA générative ou des agents
d'IA, ou qui en développent pour d'autres, et doivent montrer comment cette IA
est encadrée. Les preuves sont organisées autour du règlement européen sur l'IA
(EU AI Act) et du RGPD. S'en servent : le responsable gouvernance ou
conformité, le développeur qui branche l'application, et l'auditeur, qui ne
fait que lire. RADAR n'est pas prévu pour surveiller en direct des systèmes
biométriques, de reconnaissance des émotions, de vision par ordinateur ou des
systèmes physiques.

## Ce que fait un client

1. Il installe RADAR sur son propre serveur, où les données restent, avec une
   licence d'évaluation de trente jours.
2. Il crée les comptes (lecteur, opérateur, administrateur), protégés par un mot
   de passe et, pour les comptes à privilèges, un code à six chiffres.
3. Il inscrit l'application au registre : à quoi elle sert, ce qui lui est
   interdit, qui en répond. Par exemple : « elle ne décide jamais seule d'un
   remboursement ».
4. RADAR lui pose les questions des deux textes : pour chaque point tiré du
   règlement sur l'IA et du RGPD, il dit s'il s'applique et pourquoi. Il
   désigne aussi qui contrôle l'application, avec quels pouvoirs.
5. Le développeur branche l'application en quelques lignes de code. Dès lors,
   chaque action de l'IA envoie une fiche à RADAR : ce qu'elle a fait, et si un
   humain est intervenu.
6. RADAR enregistre chaque fiche sous scellé, puis l'analyse. Des signaux
   ressortent, par exemple un IBAN dans une conversation, ou une décision prise
   sans la validation humaine exigée.
7. Une personne désignée prend le signal dans sa file d'examen, décide et écrit
   son motif.
8. Si c'est grave, elle ouvre un incident : les faits, l'impact, une action
   corrective avec un responsable et une échéance, et la décision, consignée, de
   prévenir ou non une autorité.
9. Le jour où on lui demande des comptes, l'entreprise génère un dossier de
   preuves pour une application et une période, en PDF, en page web et en
   données, en français et en anglais : ce qu'est le système, ce qu'il a fait,
   ce que les humains ont décidé, ce qui manque.
10. L'auditeur voit qui a décidé quoi et quand, et le contrôle d'intégrité de
    RADAR montre si un enregistrement a été modifié depuis.

RADAR montre aussi, pour chaque exigence, les preuves présentes ou manquantes,
et gère la conservation, le gel, la suppression contrôlée, la sauvegarde et la
restauration. Après la licence, les données restent lisibles et exportables ;
plus rien de nouveau n'est enregistré.

## Comment RADAR se branche sur une IA

RADAR ne se place pas entre l'application et le modèle. Il n'intercepte aucun
appel et ne parle jamais au modèle.

C'est l'application qui raconte ce qui vient de se passer. Là où l'IA agit, le
développeur ajoute un appel qui envoie une fiche : le système et sa version, le
type d'action, si un humain est intervenu, et le contenu que l'entreprise a
choisi de transmettre. Pour chaque système, elle règle le sort du contenu brut :
conservé, masqué quand c'est possible, ou écarté après analyse. L'appel passe
par la bibliothèque Python fournie avec RADAR, ou par une simple requête HTTP
depuis n'importe quel langage.

Trois conséquences :

- RADAR ne dépend ni d'un modèle, ni d'un fournisseur, ni de la façon dont
  l'agent est construit. Les combinaisons prises en charge figurent dans la
  matrice de compatibilité livrée avec le produit.
- RADAR n'a aucune prise sur l'application. S'il est arrêté, elle continue de
  fonctionner ; la bibliothèque Python garde les fiches et les renvoie ensuite.
- RADAR ne voit que ce qu'on lui envoie. Il signale un trou dans la suite des
  fiches ou une fiche en retard, mais ne peut pas deviner une fiche jamais
  envoyée.

## Ce que RADAR garantit, et ce qu'il ne garantit pas

- **Une analyse déterministe.** Pas d'IA générative, mais des règles écrites :
  détecteurs de données personnelles, contrôles fixes, et politiques de
  surveillance réglées par l'entreprise. La même fiche donne toujours le même
  résultat, et chaque résultat dit quelle règle, dans quelle version, l'a
  produit.
- **Un signal est un indice, pas un jugement.** RADAR écrit « IBAN possible »,
  pas « donnée personnelle avérée ». Un humain tranche, et c'est sa décision qui
  est conservée.
- **Pas de promesse de tout détecter.** Une règle ne trouve que ce pour quoi
  elle est écrite, et l'absence de signal ne prouve pas l'absence de problème.
  Le produit le dit à côté de chaque résultat et dans chaque dossier de preuves.
- **Scellé, pas inaltérable.** Une modification ultérieure se verrait au
  contrôle d'intégrité. RADAR n'est pas pour autant le témoin de ce qu'on ne lui
  a pas envoyé.
- **Ce qu'il ne fait pas, et c'est voulu.** RADAR ne bloque ni ne filtre l'IA.
  Il ne certifie pas la conformité, ne remplace pas un conseil juridique, ne
  fixe pas le rôle juridique de l'entreprise, ne prévient aucune autorité à sa
  place et ne décide jamais à la place d'un humain.

Ce que l'entreprise obtient, c'est la preuve qu'elle surveille son IA avec une
méthode, que des personnes nommées examinent et décident, et qu'une réécriture
après coup se verrait.

## Où en est RADAR, et comment y accéder

RADAR est en accès anticipé, sur demande, pour les entreprises établies en
France. Après une courte qualification, l'entreprise mène une évaluation
autonome de trente jours sur sa propre infrastructure, selon des conditions
convenues par écrit. Pas de téléchargement public, pas de vente en ligne. La
suite fait l'objet d'un accord écrit distinct.

Demander un accès : <https://www.akioud.ai/fr/contact>

## Code source

Le code source de RADAR est propriétaire et ne figure pas dans ce dépôt. Voir
[LICENSE](LICENSE).

RADAR est conçu par AKIOUD AI, société française. <https://www.akioud.ai/fr>
