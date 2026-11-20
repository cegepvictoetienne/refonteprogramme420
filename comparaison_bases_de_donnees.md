# Bases de données 1 et 2 — version initiale vs version actuelle

- **Version initiale** : commit `2ae1105` « Version initiale » (2026-08-24)
- **Version actuelle** : fichiers de travail au 2026-11-09 (dernier commit `f229f9b` du 2026-10-23 **+ modifications non commitées** : retrait de critères d'évaluation et correction des incohérences dans les deux cours)
- Bases de données 2 s'appelait `420-3B4-VI` avant le renumérotage SOBEC (commit `b10c29d`) ; il est maintenant `420-3D4-VI`.

---

## Bases de données 1 (420-2B4-VI)

Durée, pondération et unités inchangées : 60 h, 2-2-2, 2 unités.

| Section | Version initiale | Version actuelle |
|---|---|---|
| NEJ | — | Ajouté (théorie 30, lab 30, théorie-lab 30 ; raison pédagogique vide) |
| Préalables | Programmation 1 (420-1D6-VI) + Développement Web 1 (corequis) | Développement Web 1 (corequis) seulement |
| Préalable à | BD 2 (420-3B4-VI), Piratage éthique (420-3C4-VI) | BD 2 (420-3D4-VI), Sécurité informatique (420-3F4-VI) |
| Éléments de compétence 00Q7 | 1, 2, 3, 4, 5 | 1, 2, 3, 5 — **élément 4 (traitements automatisés) retiré** |
| Épreuve finale — à produire | Scripts de déclencheurs et de procédures stockées + requêtes | Scripts de **vues** et de **création d'utilisateurs/rôles** + requêtes |
| Critères d'évaluation | 7 critères | 4 critères (retirés : analyse des spécifications du SGBD, procédures stockées, documentation d'aide à la programmation ; « déclencheurs » remplacé par « vues ») |
| Notes préliminaires | Suite : BD 2 (420-3B4-VI), Mégadonnées (420-4C4-VI) | Suite : BD 2 (420-3D4-VI), Bases de données non-relationelles (420-4C4-VI) |
| Médiagraphie / démarche | — | Inchangées |
| Description pour diagramme | — | « MySQL, jointure, vues, CRUD » |

### Répartition des heures par élément

| Élément | Initiale | Actuelle | Contenu essentiel |
|---|---:|---:|---|
| 00Q7-1 Créer la BD | 8 | 12 | inchangé |
| 00Q7-2 Requêtes CRUD | 16 | 24 | + Vues |
| 00Q7-3 Confidentialité et cohérence | 12 | 16 | − déclencheurs (TRIGGER), − transactions |
| 00Q7-4 Traitements automatisés | 20 | — | élément retiré (procédures, fonctions) |
| 00Q7-5 Sauvegarde/restauration | 4 | 8 | + validation de sauvegarde, restauration |
| **Total** | **60** | **60** | |

**En résumé** : BD1 devient un cours centré sur SQL (création, CRUD, vues, sécurité, sauvegarde). La programmation côté serveur (déclencheurs, transactions, procédures/fonctions) passe en BD2.

---

## Bases de données 2 (420-3B4-VI → 420-3D4-VI)

| Section | Version initiale | Version actuelle |
|---|---|---|
| Code | 420-3B4-VI | 420-3D4-VI |
| Durée / pondération / unités | 60 h, 2-2-2, 2 unités | **45 h, 1-2-2, 1 unité** |
| NEJ | — | Ajouté (théorie 30, lab 30, théorie-lab 30 ; raison pédagogique vide) |
| Préalable à | Conception de systèmes (420-4B4-VI), Mégadonnées (420-4C4-VI) | Architecture logicielle et AQ (420-4F4-VI), BD non-relationnelles (420-4G4-VI) |
| Compétences | 00Q6 (POO, éléments 1 à 7) + 00Q7 (1, 2, 3, 4) | **00Q7 seulement** (1, 3, 4) — 00Q6 retirée, 00Q7-2 retiré |
| Épreuve finale — partie 1 | Modélisation **et création** : modèle, script de création, déclencheurs, utilisateur et autorisations | Modélisation seulement (relations et table pivot) : l'élève produit le modèle |
| Épreuve finale — partie 2 | Transaction, procédure stockée, jointures, encryption | Transaction, procédure stockée, **déclencheur et fonction** |
| Critères d'évaluation | 14 critères | 7 critères (retirés notamment : analyse des spécifications du SGBD, création de la BD, déclencheurs, expressions régulières, fonctionnement des requêtes, choix des types/structures, documentation) |
| Médiagraphie | Notes de cours numériques | Documentation MySQL (dev.mysql.com/doc) |
| Description pour diagramme | — | « Modélisation, Procédures stockées, déclencheurs » |

### Répartition des heures par élément

| Élément | Initiale | Actuelle | Contenu essentiel |
|---|---:|---:|---|
| 00Q6-1 à 00Q6-7 (POO : analyse, modélisation, algorithmes, interface, PHP-mysqli, documentation, migrations) | 20 | — | compétence retirée |
| 00Q7-1 Créer la BD | 6 | 15 | « CREATE TABLE; INDEX; VIEW » → « Schéma conceptuel, schéma relationnel » |
| 00Q7-2 Requêtes avancées (jointures, REGEX, EXISTS…) | 20 | — | élément retiré |
| 00Q7-3 Confidentialité et cohérence | 4 | 10 | − gestion des utilisateurs (phpMyAdmin), − contraintes d'intégrité ; + déclencheurs (venus de 00Q7-4) |
| 00Q7-4 Traitements automatisés | 10 | 20 | − déclencheurs ; + fonctions |
| **Total** | **60** | **45** | |

**En résumé** : BD2 perd la partie programmation orientée objet / PHP et les requêtes avancées, et se recentre sur la modélisation, les déclencheurs, les transactions/encryption et les procédures/fonctions stockées.

---

## Diffs complets

<details>
<summary>Bases de données 1 — diff complet</summary>

```diff
--- 420-2B4-VI.yaml (version initiale, 2ae1105)
+++ 420-2B4-VI.yaml (version actuelle)
@@ -1,5 +1,11 @@
 code: 420-2B4-VI
 titre: Bases de données 1
+NEJ:
+  - theorie: 30
+  - lab: 30
+  - theorie-lab: 30
+  - raison_pedagogique: >-
+     
 programme:
   numero: "420"
   nom: Techniques de l'informatique
@@ -9,16 +15,14 @@
   - Lagacé, Christiane
   - Taleb, Frédérik
 prealables:
-  - cours: 420-1D6-VI
-    titre: Programmation 1
   - cours: 420-2A4-VI
     titre: Développement Web 1
     type: Corequis
 prealable_a:
-  - cours: 420-3B4-VI
+  - cours: 420-3D4-VI
     titre: Bases de données 2
-  - cours: 420-3C4-VI
-    titre: Piratage éthique
+  - cours: 420-3F4-VI
+    titre: Sécurité informatique
 note_prealables: >-
   Ce cours pourrait également être préalable aux cours qui ont un préalable
   spécial.
@@ -37,7 +41,6 @@
       - "1 - Créer la base de données"
       - "2 - Formuler des requêtes de lecture, d'insertion, de modification et de suppression de données"
       - "3 - Assurer la confidentialité et la cohérence des données"
-      - "4 - Programmer des traitements de données automatisés"
       - "5 - Sauvegarder et restaurer la base de données"
 
 cible_formation: >-
@@ -57,9 +60,9 @@
   est vue partiellement.
 
 
-  Son atteinte sera complétée dans les cours suivants : 420-3B4-VI : Bases
+  Son atteinte sera complétée dans les cours suivants : 420-3D4-VI : Bases
   de données 2 à la 3e session (profil B0 : Profil par défaut); 420-4C4-VI
-  : Mégadonnées à la 4e session (profil B0 : Profil par défaut).
+  : Bases de données non-relationelles à la 4e session (profil B0 : Profil par défaut).
 
 
   Le système de gestion de base de données ciblé pour ce cours est MySQL
@@ -71,8 +74,8 @@
   ponderation: "50 %"
   performance_finale_exigee: >-
     À partir d'une mise en situation et du modèle fourni, l'élève aura à
-    produire : le script de création des déclencheurs; le script de
-    création des procédures stockées; les requêtes de vérification et
+    produire : le script de création des vues; le script de
+    création des utilisateurs et des rôles; les requêtes de vérification et
     implanter sa solution dans un système de gestion de base de données.
   contexte_realisation: >-
     L'épreuve finale sera un examen individuel d'une durée de 2 heures en
@@ -81,13 +84,10 @@
     bases de données pour produire ses scripts et implanter sa solution.
     Les notes de cours fournies par l'enseignant.e seront permises.
   criteres_evaluation:
-    - Analyse juste des spécifications du système de gestion de base de données
-    - Utilisation appropriée des contraintes d'intégrité référentielle, des déclencheurs
+    - Utilisation appropriée des contraintes d'intégrité référentielle, des vues
     - Détermination judicieuse des types de requêtes à formuler
     - Utilisation appropriée des clauses, des opérateurs, des commandes ou des paramètres
     - Fonctionnement correct des requêtes
-    - Création appropriée de procédures stockées ou de scripts
-    - Notation claire de la documentation d'aide à la programmation
 
 demarche_pedagogique_suggeree: >-
   Théorie, démonstrations, et auto-apprentissage, informations complétées à
@@ -103,7 +103,7 @@
 elements_competence:
   - code: 00Q7-1
     titre: "Créer la base de données"
-    duree_heures: 8
+    duree_heures: 12
     habiletes:
       - "Formuler les instructions de création de la base de données"
     criteres_performance:
@@ -116,7 +116,7 @@
       (AUTO INCREMENT)
   - code: 00Q7-2
     titre: "Formuler des requêtes de lecture, d'insertion, de modification et de suppression de données"
-    duree_heures: 16
+    duree_heures: 24
     habiletes:
       - "Déterminer les types de requêtes à formuler"
       - "Utiliser les clauses, les opérateurs, les commandes ou les paramètres"
@@ -133,10 +133,10 @@
       opérateurs de filtrage (BETWEEN, IN); opérateur de comparaison avec un
       modèle ou expression régulière (LIKE, REGEXP); fonctions statistiques
       (MIN, MAX, AVG, COUNT, SUM); clause d'agrégation (GROUP BY); opérateur
-      de filtrage pour agrégat (HAVING)
+      de filtrage pour agrégat (HAVING); Vues
   - code: 00Q7-3
     titre: "Assurer la confidentialité et la cohérence des données"
-    duree_heures: 12
+    duree_heures: 16
     habiletes:
       - "Déterminer les techniques à utiliser"
       - "Gérer les autorisations"
@@ -152,25 +152,10 @@
       modification des droits d'accès, …); gestion des accès aux tables
       (lecture, écriture, modification des droits d'accès, …); types de
       cryptage; contraintes d'intégrité (FOREIGN KEY, UNIQUE, CHECK,
-      DEFAULT); déclencheur (TRIGGER); transaction (COMMIT, ROLLBACK, …)
-  - code: 00Q7-4
-    titre: "Programmer des traitements de données automatisés"
-    duree_heures: 20
-    habiletes:
-      - "Déterminer les traitements de données à automatiser"
-      - "Créer les procédures stockées ou les scripts"
-      - "Annoter la documentation d'aide à la programmation"
-    criteres_performance:
-      - "1 - Détermination judicieuse des traitements de données à automatiser"
-      - "2 - Création appropriée de procédures stockées ou de scripts"
-      - "3 - Notation claire de la documentation d'aide à la programmation"
-    contenu_essentiel: >-
-      Fonctions intégrées au système de gestion de base de données (DATE,
-      TIME, IF, …); création de procédures (CREATE PROCEDURE); création de
-      fonctions (CREATE FONCTION); produire le script annoté
+      DEFAULT); 
   - code: 00Q7-5
     titre: "Sauvegarder et restaurer la base de données"
-    duree_heures: 4
+    duree_heures: 8
     habiletes:
       - "Choisir les techniques de sauvegarde et de restauration à utiliser"
       - "Utiliser les techniques de sauvegarde et de restauration de la base de données"
@@ -181,4 +166,7 @@
       - "3 - Respect de la procédure et de la fréquence de sauvegarde"
     contenu_essentiel: >-
       Clause de sauvegarde de la base de données (BACKUP DATABASE);
-      automatisation de la sauvegarde; gestion des fichiers de sauvegarde
+      automatisation de la sauvegarde; gestion des fichiers de sauvegarde; Validation de sauvegarde;
+      Restauration de la base de données;
+description_dans_diagramme: >-
+  MySQL, jointure, vues, CRUD
```

</details>

<details>
<summary>Bases de données 2 — diff complet</summary>

```diff
--- 420-3B4-VI.yaml (version initiale, 2ae1105)
+++ 420-3D4-VI.yaml (version actuelle)
@@ -1,5 +1,11 @@
-code: 420-3B4-VI
+code: 420-3D4-VI
 titre: Bases de données 2
+NEJ:
+  - theorie: 30
+  - lab: 30
+  - theorie-lab: 30
+  - raison_pedagogique: >-
+     
 programme:
   numero: "420"
   nom: Techniques de l'informatique
@@ -13,37 +19,26 @@
   - cours: 420-2B4-VI
     titre: Bases de données 1
 prealable_a:
-  - cours: 420-4B4-VI
-    titre: Conception de systèmes
-  - cours: 420-4C4-VI
-    titre: Mégadonnées
+  - cours: 420-4F4-VI
+    titre: Architecture logicielle et assurance qualité
+  - cours: 420-4G4-VI
+    titre: Bases de données non-relationelles
 note_prealables: >-
   Ce cours pourrait également être préalable aux cours qui ont un préalable
   spécial.
-duree_heures: 60
-ponderation: "2-2-2"
-unites: 2
+duree_heures: 45
+ponderation: "1-2-2"
+unites: 1
 dates:
   analyse_equipe_programme: 2020-02-19
   adoption_departement: 2020-04-02
   approbation_service_etudes: 2022-06-15
 
 competences:
-  - code: 00Q6
-    titre: "Exploiter les principes de la programmation orientée objet"
-    elements:
-      - "1 - Analyser le problème"
-      - "2 - Modéliser les classes"
-      - "3 - Produire les algorithmes pour les méthodes"
-      - "4 - Générer l'interface graphique"
-      - "5 - Programmer des classes"
-      - "6 - Documenter la programmation"
-      - "7 - Appliquer la procédure liée à la gestion des versions de programmes"
   - code: 00Q7
     titre: "Exploiter un système de gestion de base de données"
     elements:
       - "1 - Créer la base de données"
-      - "2 - Formuler des requêtes de lecture, d'insertion, de modification et de suppression de données"
       - "3 - Assurer la confidentialité et la cohérence des données"
       - "4 - Programmer des traitements de données automatisés"
 
@@ -52,7 +47,7 @@
   classes et de concevoir et exploiter une base de données.
 
 notes_preliminaires: >-
-  Le cours 420-3B4-VI : Bases de données 2 fait partie de la formation
+  Le cours 420-3D4-VI : Bases de données 2 fait partie de la formation
   menant au diplôme d'études collégiales (DEC) dans le programme 420.B0 :
   Techniques de l'informatique.
 
@@ -60,21 +55,6 @@
   Il est offert en 3e session.
 
 
-  Plusieurs compétences sont touchées par ce cours.
-
-
-  La compétence 00Q6 : Exploiter les principes de la programmation
-  orientée objet est vue partiellement.
-
-
-  Son acquisition a débuté dans le cours 420-2A6-VI : Programmation 2 à la
-  2e session.
-
-
-  Son acquisition sera complétée dans le cours 420-4A6-VI : Programmation
-  3 à la 4e session.
-
-
   La compétence 00Q7 : Exploiter un système de gestion de base de données
   est vue partiellement.
 
@@ -83,46 +63,36 @@
   la 2e session.
 
 
-  Son acquisition sera complétée dans le cours 420-4C4-VI : Mégadonnées à
+  Son acquisition sera complétée dans le cours 420-4C4-VI : Bases de données non-relationelles à
   la 4e session.
 
 epreuve_finale:
   ponderation: "50 %"
   performance_finale_exigee: >-
-    Partie 1 : Modélisation et création de la base de données : modèle
-    avec relations et table pivot, au moins un déclencheur, création d'un
-    utilisateur et de ses autorisations. L'élève aura à produire : le
-    modèle de la base de données; le script de création de la base de
-    données; le script de création des déclencheurs; le script de création
-    d'un utilisateur et de modifications de ses autorisations.
+    Partie 1 : Modélisation de la base de données : modèle
+    avec relations et table pivot
+    L'élève aura à produire : le modèle de la base de données.
 
 
     Partie 2 : Exploitation de la base de données : transaction, procédure
-    stockée, jointures et encryption à partir d'une base de données fournie
+    stockée, un déclencheur et fonction à partir d'une base de données fournie
     et d'un modèle complexe. L'élève aura à produire : le script de
-    création des procédures stockées; les requêtes de vérification;
+    création des procédures stockées, déclencheur et fonctions; les requêtes de vérification;
     l'implémentation des scénarios exigés pour exploiter la base de
     données.
   contexte_realisation: >-
-    L'épreuve finale est un examen individuel en 2 parties, à la fin
+    L'épreuve finale est un examen individuel en 2 parties, à la
     semaine 15. Chaque partie est complétée en classe et dure 2 périodes.
     Le matériel permis est : notes de cours de l'enseignant.e, notes de
     cours de l'élève et site web du cours.
   criteres_evaluation:
     - Conception juste du modèle de données
-    - Analyse juste des spécifications du système de gestion de base de données
-    - Formulation appropriée des instructions de création de la base de données
-    - Utilisation appropriée des contraintes d'intégrité référentielle, des déclencheurs
     - Détermination judicieuse des types de requêtes à formuler
     - Utilisation appropriée des clauses, des opérateurs, des commandes ou des paramètres
-    - Utilisation appropriée des expressions régulières
-    - Fonctionnement correct des requêtes
-    - Création appropriée de procédures stockées ou de scripts
-    - Choix approprié des instructions, des types de données élémentaires et des structures de données
+    - Création appropriée de procédures stockées ou de fonctions
     - Organisation logique des instructions
     - Respect de la syntaxe du langage
     - Respect des règles de codage
-    - Notation claire de la documentation d'aide à la programmation
 
 demarche_pedagogique_suggeree: >-
   Courtes périodes d'enseignement théorique suivies d'application au fur et
@@ -137,121 +107,15 @@
   absolument les compléter afin d'être prêts pour l'épreuve finale.
 
 mediagraphie:
-  - "Notes de cours fournies en format numérique"
+  - "Documentation MySQL : https://dev.mysql.com/doc"
 
 materiel_requis: >-
   Un ordinateur portable
 
 elements_competence:
-  - code: 00Q6-1
-    titre: "Analyser le problème"
-    duree_heures: 4
-    habiletes:
-      - "Décomposer un problème en fonction des exigences de l'approche relationnelle"
-      - "Déterminer les données d'entrée et de sortie ainsi que de la nature des traitements"
-      - "Déterminer les classes à modéliser"
-      - "Déterminer les relations entre les classes"
-    criteres_performance:
-      - "1 - Décomposition du problème en fonction des exigences de l'approche relationnelle"
-      - "2 - Détermination correcte des données d'entrée, des données de sortie et de la nature des traitements"
-      - "3 - Détermination juste des classes à modéliser"
-      - "4 - Détermination correcte des relations entre les classes"
-    contenu_essentiel: >-
-      Modèle entité-relation; diagramme de classes; formes normales; types
-      de relations (1:n, n:n)
-  - code: 00Q6-2
-    titre: "Modéliser les classes"
-    duree_heures: 4
-    habiletes:
-      - "Déterminer les attributs des classes"
-      - "Déterminer les types des attributs"
-      - "Représenter les classes et leurs relations de façon graphique"
-      - "Respecter les règles de nomenclature"
-    criteres_performance:
-      - "1 - Détermination correcte des attributs des classes"
-      - "2 - Détermination correcte des types des attributs"
-      - "3 - Représentation graphique correcte des classes et de leurs relations"
-      - "4 - Respect des règles de nomenclature"
-    contenu_essentiel: >-
-      Création d'une classe (attributs, types, propriétés, contraintes
-      d'intégrité); respect d'une nomenclature; production du modèle
-      entité-relation; production du diagramme UML des classes avec les
-      relations entre elles.
-  - code: 00Q6-3
-    titre: "Produire les algorithmes"
-    duree_heures: 2
-    habiletes:
-      - "Déterminer une séquence logique des opérations nécessaires pour chaque algorithme"
-      - "Déterminer une séquence logique des opérations"
-      - "Vérifier le fonctionnement des algorithmes"
-      - "Schématiser les algorithmes sur papier"
-    criteres_performance:
-      - "1 - Détermination adéquate des opérations nécessaires pour chaque algorithme"
-      - "2 - Détermination correcte d'une séquence logique des opérations"
-      - "3 - Vérification appropriée du fonctionnement des algorithmes"
-      - "4 - Représentation correcte des algorithmes"
-    contenu_essentiel: >-
-      Opérateurs arithmétiques et logiques; conditions; boucles; procédures
-      et fonctions stockées; triggers
-  - code: 00Q6-4
-    titre: "Générer l'interface graphique"
-    duree_heures: 2
-    habiletes:
-      - "Choisir les éléments graphiques utiles à l'affichage de la saisie"
-      - "Positionner ergonomiquement les éléments graphiques"
-      - "Paramétrer les éléments graphiques"
-    criteres_performance:
-      - "1 - Choix approprié des éléments graphiques pour l'affichage et la saisie"
-      - "2 - Positionnement correct des éléments graphiques"
-      - "3 - Paramétrage correct des éléments graphiques"
-    contenu_essentiel: >-
-      Tableaux; formulaires; boutons
-  - code: 00Q6-5
-    titre: "Programmer les interactions avec la base de données"
-    duree_heures: 4
-    habiletes:
-      - "Choisir les instructions, les types de données, et structures de données"
-      - "Organiser les instructions"
-      - "Programmer les messages à afficher à l'utilisatrice ou à l'utilisateur"
-      - "Respecter la syntaxe du langage et les règles du code"
-    criteres_performance:
-      - "1 - Choix approprié des instructions, des types de données élémentaires et des structures de données"
-      - "2 - Organisation logique des instructions"
-      - "3 - Programmation correcte des messages à afficher à l'utilisatrice ou à l'utilisateur"
-      - "4 - Fonctionnement correct du programme"
-      - "5 - Respect de la syntaxe du langage"
-      - "6 - Respect des règles de codage"
-    contenu_essentiel: >-
-      PHP - mysqli; passage de paramètres; curseur; exceptions
-  - code: 00Q6-6
-    titre: "Documenter la programmation"
-    duree_heures: 2
-    habiletes:
-      - "Commenter le code"
-      - "Documenter le programme"
-      - "Utiliser des générateurs de documentation"
-    criteres_performance:
-      - "1 - Notation claire de commentaires dans le code informatique"
-      - "2 - Notation claire de la documentation d'aide à la programmation"
-      - "3 - Utilisation appropriée des générateurs de documentation"
-    contenu_essentiel: >-
-      phpDocumentor; commentaires sur le diagramme
-  - code: 00Q6-7
-    titre: "Appliquer la procédure liée à la gestion des versions de programmes"
-    duree_heures: 2
-    habiletes:
-      - "Configurer le système de migration"
-      - "Soumettre le code modifié"
-      - "Gérer les modifications structurelles de la base de données"
-    criteres_performance:
-      - "1 - Configuration correcte du système de migration"
-      - "2 - Soumission méthodique du code modifié"
-      - "3 - Gestion judicieuse des modifications structurelles de la base de données"
-    contenu_essentiel: >-
-      Outil de migration et de mise à jour de base de données
   - code: 00Q7-1
     titre: "Créer la base de données"
-    duree_heures: 6
+    duree_heures: 15
     habiletes:
       - "Analyser le modèle de données"
       - "Analyser les spécifications du système de gestion de base de données"
@@ -261,26 +125,10 @@
       - "2 - Analyse juste des spécifications du système de gestion de base de données"
       - "3 - Formulation appropriée des instructions de création de la base de données"
     contenu_essentiel: >-
-      CREATE TABLE; INDEX; VIEW
-  - code: 00Q7-2
-    titre: "Formuler des requêtes de lecture, d'insertion, de modification et de suppression de données"
-    duree_heures: 20
-    habiletes:
-      - "Déterminer les types de requêtes à formuler"
-      - "Utiliser des clauses, des opérateurs, des commandes ou des paramètres"
-      - "Utiliser les expressions régulières"
-    criteres_performance:
-      - "1 - Détermination judicieuse des types de requêtes à formuler"
-      - "2 - Utilisation appropriée des clauses, des opérateurs, des commandes ou des paramètres"
-      - "3 - Utilisation appropriée des expressions régulières"
-      - "4 - Fonctionnement correct des requêtes"
-    contenu_essentiel: >-
-      Commandes SQL avancées; INSERT INTO SELECT; UPDATE avec champ de
-      référence; GROUP BY avec HAVING; REGEX; IFNULL(); EXISTS(); jointures
-      (INNER JOIN, LEFT JOIN, RIGHT JOIN, UNION)
+      Schéma conceptuel, schéma relationnel;
   - code: 00Q7-3
     titre: "Assurer la confidentialité et la cohérence des données"
-    duree_heures: 4
+    duree_heures: 10
     habiletes:
       - "Déterminer les techniques à utiliser"
       - "Gérer les autorisations"
@@ -292,12 +140,13 @@
       - "3 - Cryptage approprié des données"
       - "4 - Utilisation appropriée des contraintes d'intégrité référentielle, des déclencheurs ou des transactions"
     contenu_essentiel: >-
-      Gestion des utilisateurs et des autorisations avec Phpmyadmin;
-      contraintes d'intégrité référentielle; transactions; encryption
-      complète avec clé
+      transactions; encryption
+      complète avec clé;
+      déclencheurs (BEFORE (INSERT, UPDATE, DELETE), AFTER (INSERT, UPDATE,
+      DELETE))
   - code: 00Q7-4
     titre: "Programmer des traitements de données automatisés"
-    duree_heures: 10
+    duree_heures: 20
     habiletes:
       - "Déterminer les traitements de données à automatiser"
       - "Créer des procédures stockées"
@@ -310,5 +159,6 @@
       - "3 - Notation claire de la documentation d'aide à la programmation"
     contenu_essentiel: >-
       Procédures stockées, paramètres et valeurs de retour; curseurs;
-      déclencheurs (BEFORE (INSERT, UPDATE, DELETE), AFTER (INSERT, UPDATE,
-      DELETE))
+      Fonctions
+description_dans_diagramme: >-
+  Modélisation, Procédures stockées, déclencheurs
```

</details>
