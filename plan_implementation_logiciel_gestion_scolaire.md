# Plan d’implémentation — Logiciel de gestion scolaire

## 1. Vision du produit

Créer un logiciel SaaS de gestion scolaire moderne, complet, simple à utiliser et adapté aux établissements scolaires.

Le logiciel doit centraliser la gestion administrative, pédagogique et financière d’une école, avec une architecture évolutive et sécurisée.

### Principes fondamentaux

- Interface moderne, claire et responsive.
- Architecture SaaS multi-écoles (multi-tenant).
- Séparation stricte des données entre établissements.
- Gestion par année scolaire.
- Historique des élèves conservé d’une année à l’autre.
- Traçabilité des opérations importantes.
- Permissions contrôlées côté backend.
- Aucun effacement définitif des données sensibles.
- Export PDF, Excel et CSV.
- Import Excel/CSV avec validation préalable.
- Recherche globale rapide.
- Prévoir une architecture compatible avec une évolution future vers mobile, SMS, Mobile Money et autres services.

---

# 2. Utilisateurs du logiciel

Le logiciel possède exactement **3 types d’utilisateurs**.

## 2.1 Direction

La Direction dispose du contrôle global de l’établissement.

Elle peut :

- consulter et gérer les élèves ;
- gérer les admissions et inscriptions ;
- gérer les classes ;
- gérer les enseignants ;
- gérer les matières ;
- consulter et gérer les emplois du temps ;
- consulter et contrôler les présences ;
- consulter et contrôler les notes ;
- gérer les examens ;
- consulter et générer les bulletins ;
- gérer les frais scolaires ;
- consulter les paiements ;
- gérer la caisse ;
- gérer les dépenses ;
- consulter la comptabilité ;
- consulter les impayés ;
- gérer les documents ;
- gérer les communications ;
- consulter tous les rapports ;
- gérer les utilisateurs ;
- gérer les paramètres ;
- consulter le journal d’activité.

## 2.2 Secrétariat

Le Secrétariat regroupe les fonctions :

- administratives ;
- caisse ;
- comptabilité.

Il peut notamment :

- créer et modifier les dossiers élèves ;
- gérer les admissions ;
- gérer les inscriptions ;
- gérer les réinscriptions ;
- gérer les classes selon les permissions accordées ;
- gérer les dossiers administratifs ;
- enregistrer les paiements ;
- éditer les reçus ;
- gérer la caisse ;
- enregistrer les recettes ;
- enregistrer les dépenses ;
- suivre les impayés ;
- consulter et gérer les informations financières ;
- générer les documents administratifs ;
- consulter les rapports autorisés.

Le système doit permettre de configurer des permissions différentes pour plusieurs secrétaires, sans créer de nouveaux types d’utilisateurs.

## 2.3 Professeur

Le professeur est principalement orienté vers la gestion pédagogique.

Il peut :

- consulter son emploi du temps ;
- consulter ses classes ;
- consulter les élèves de ses classes ;
- faire l’appel ;
- enregistrer les présences ;
- saisir les notes ;
- consulter les évaluations qui le concernent ;
- gérer les devoirs ;
- consulter les résultats nécessaires à son travail ;
- consulter/générer les informations pédagogiques autorisées.

Le professeur ne doit pas avoir accès aux fonctions financières.

---

# 3. Modules principaux

Le logiciel sera organisé autour des modules suivants :

1. Tableau de bord
2. Scolarité
3. Pédagogie
4. Finance
5. Documents
6. Communication
7. Rapports
8. Administration

---

# 4. Module Tableau de bord

## Direction

Afficher :

- nombre total d’élèves ;
- nouveaux élèves ;
- inscriptions en attente ;
- dossiers incomplets ;
- nombre d’enseignants ;
- classes ;
- présence du jour ;
- moyenne générale ;
- recettes ;
- dépenses ;
- solde de caisse ;
- montant total des impayés ;
- paiements récents ;
- alertes importantes.

Le tableau de bord doit également afficher des alertes actionnables, par exemple :

- « 27 dossiers incomplets »
- « 43 élèves ont un solde impayé »
- « 8 enseignants n’ont pas encore terminé la saisie des notes »

## Secrétariat

Afficher notamment :

- admissions récentes ;
- dossiers à compléter ;
- inscriptions ;
- paiements récents ;
- reçus ;
- impayés ;
- état de caisse ;
- dépenses ;
- actions rapides.

## Professeur

Afficher :

- cours du jour ;
- prochaines heures de cours ;
- classes du jour ;
- appels à effectuer ;
- notes à saisir ;
- évaluations à venir ;
- devoirs.

---

# 5. Module Scolarité

## 5.1 Élèves

Chaque élève possède un dossier permanent.

Informations principales :

- matricule ;
- nom ;
- prénom ;
- sexe ;
- date de naissance ;
- lieu de naissance ;
- nationalité ;
- adresse ;
- téléphone éventuel ;
- photo ;
- date d’admission ;
- statut ;
- documents ;
- informations des responsables/tuteurs.

### Règle importante

Un élève ne doit pas être recréé chaque année.

Son dossier reste permanent.

Exemple d’historique :

- 2024-2025 → 6e A
- 2025-2026 → 5e A
- 2026-2027 → 4e B

## 5.2 Responsables / tuteurs

Les responsables existent uniquement comme informations liées à l’élève.

Ils ne disposent pas de compte utilisateur dans cette version.

Prévoir :

- nom ;
- prénom ;
- relation avec l’élève ;
- téléphone ;
- email ;
- profession ;
- adresse ;
- responsable principal ou secondaire.

## 5.3 Admissions

Workflow :

**Demande → Dossier → Vérification → Acceptation → Inscription**

Statuts possibles :

- brouillon ;
- en attente ;
- dossier incomplet ;
- vérifié ;
- accepté ;
- refusé ;
- annulé.

## 5.4 Inscriptions

Gérer :

- inscription initiale ;
- réinscription ;
- transfert ;
- changement de classe ;
- changement de niveau ;
- promotion ;
- redoublement ;
- abandon ;
- exclusion.

## 5.5 Classes

Une classe doit contenir :

- niveau ;
- nom ;
- année scolaire ;
- salle ;
- professeur principal éventuel ;
- effectif ;
- matières associées.

## 5.6 Enseignants

Gérer :

- identité ;
- coordonnées ;
- spécialités ;
- matières ;
- classes ;
- statut ;
- historique d’affectation.

## 5.7 Matières

Gérer :

- nom ;
- code ;
- niveau ;
- coefficient ;
- enseignant(s) ;
- classe(s).

Les coefficients doivent être configurables.

---

# 6. Module Pédagogie

## 6.1 Emploi du temps

Gérer :

- classes ;
- enseignants ;
- matières ;
- salles ;
- jours ;
- heures.

Le système doit détecter automatiquement :

- conflit professeur ;
- conflit classe ;
- conflit salle.

## 6.2 Présences

Le professeur peut faire l’appel de ses classes.

Statuts :

- présent ;
- absent ;
- retard ;
- absence justifiée.

Conserver l’historique.

La Direction et le Secrétariat peuvent consulter les présences selon leurs permissions.

## 6.3 Évaluations

Créer :

- devoirs ;
- interrogations ;
- compositions ;
- examens ;
- autres évaluations.

Une évaluation possède :

- matière ;
- classe ;
- période ;
- date ;
- barème ;
- coefficient ;
- enseignant.

## 6.4 Notes

Le professeur saisit les notes de ses matières/classes.

Le système calcule :

- moyenne par matière ;
- moyenne générale ;
- coefficient ;
- classement ;
- appréciation.

Les règles de calcul doivent être configurables.

## 6.5 Examens

Gérer :

- sessions ;
- matières ;
- classes ;
- dates ;
- salles ;
- résultats.

## 6.6 Bulletins

Générer automatiquement :

- bulletin individuel ;
- relevé de notes ;
- moyenne générale ;
- classement ;
- appréciations ;
- décision éventuelle.

Les bulletins doivent être exportables en PDF.

## 6.7 Devoirs

Dans la première version :

- création d’un devoir ;
- matière ;
- classe ;
- date ;
- consigne ;
- pièce jointe éventuelle ;
- statut.

Les élèves ne disposent pas encore d’un compte pour envoyer directement leurs devoirs.

---

# 7. Module Finance

Le Secrétariat possède ici les fonctions de caisse et de comptabilité.

## 7.1 Frais scolaires

Gérer :

- types de frais ;
- frais par niveau/classe ;
- frais par année scolaire ;
- échéances ;
- remises éventuelles ;
- pénalités éventuelles.

## 7.2 Facturation

Créer :

- facture ;
- lignes de facture ;
- montant ;
- échéance ;
- statut.

Statuts :

- brouillon ;
- émise ;
- partiellement payée ;
- payée ;
- en retard ;
- annulée.

## 7.3 Paiements

Supporter :

- paiement total ;
- paiement partiel ;
- plusieurs paiements pour une même facture.

Formule :

**Solde = Total dû - Total payé**

Méthodes de paiement configurables :

- espèces ;
- virement ;
- chèque ;
- Mobile Money ;
- autre.

## 7.4 Reçus

Après un paiement :

- générer automatiquement un reçu ;
- numéro unique ;
- date ;
- élève ;
- montant ;
- mode de paiement ;
- utilisateur ayant enregistré le paiement.

Le reçu doit être exportable en PDF.

## 7.5 Caisse

Gérer :

- ouverture de caisse ;
- solde initial ;
- entrées ;
- sorties ;
- solde théorique ;
- solde réel déclaré ;
- différence ;
- clôture de caisse.

La clôture doit conserver :

- date ;
- utilisateur ;
- montant théorique ;
- montant réel ;
- écart ;
- commentaire éventuel.

## 7.6 Dépenses

Gérer :

- catégorie ;
- montant ;
- date ;
- bénéficiaire ;
- justificatif ;
- utilisateur ;
- commentaire.

## 7.7 Comptabilité

Prévoir une structure permettant :

- recettes ;
- dépenses ;
- catégories ;
- journaux ;
- périodes ;
- opérations ;
- rapports financiers.

Les transactions financières importantes ne doivent jamais être supprimées définitivement.

Une opération annulée doit rester visible avec le statut :

**CANCELLED / ANNULÉE**

## 7.8 Impayés

Afficher :

- élève ;
- classe ;
- montant dû ;
- montant payé ;
- solde ;
- échéance ;
- retard.

Prévoir filtres et export.

---

# 8. Module Documents

Gérer :

- certificats ;
- attestations ;
- relevés ;
- bulletins ;
- reçus ;
- documents administratifs ;
- archives.

Prévoir un système de modèles avec variables dynamiques.

Exemples :

```text
{{student.full_name}}
{{student.matricule}}
{{class.name}}
{{academic_year}}
{{school.name}}
```

Les documents doivent pouvoir être générés automatiquement en PDF.

---

# 9. Module Communication

MVP :

- annonces ;
- notifications internes ;
- messages internes.

Préparer l’architecture pour ajouter plus tard :

- SMS ;
- email ;
- WhatsApp ;
- notifications push.

---

# 10. Module Rapports

Rapports scolaires :

- effectifs ;
- inscriptions ;
- admissions ;
- promotions ;
- abandons ;
- transferts.

Rapports pédagogiques :

- résultats ;
- moyennes ;
- classements ;
- présences ;
- absences ;
- retards.

Rapports financiers :

- recettes ;
- dépenses ;
- paiements ;
- impayés ;
- caisse ;
- soldes ;
- statistiques.

Tous les rapports importants doivent pouvoir être exportés en :

- PDF ;
- Excel ;
- CSV.

---

# 11. Module Administration

## Utilisateurs

Exactement trois rôles :

- Direction ;
- Secrétariat ;
- Professeur.

## Permissions

Les permissions doivent être granulaires.

Exemples :

- students.view
- students.create
- students.update
- students.archive
- payments.create
- payments.view
- payments.cancel
- cash.open
- cash.close
- expenses.create
- grades.create
- grades.update
- attendance.create
- reports.finance.view

Le backend doit vérifier les permissions.

Ne jamais dépendre uniquement du frontend pour la sécurité.

## Année scolaire

Gérer :

- création ;
- ouverture ;
- période active ;
- clôture.

Une année scolaire clôturée ne doit pas pouvoir être modifiée librement.

## Paramètres

Gérer :

- informations de l’établissement ;
- logo ;
- adresse ;
- contacts ;
- année scolaire ;
- périodes ;
- règles de notation ;
- coefficients ;
- frais ;
- méthodes de paiement ;
- paramètres des documents.

## Journal d’activité

Enregistrer les actions sensibles :

- utilisateur ;
- date/heure ;
- action ;
- module ;
- objet ;
- ancienne valeur ;
- nouvelle valeur ;
- adresse IP si disponible.

Exemple :

```text
12/09/2026 10:32
Direction
Modification paiement
Paiement #PAY-00052
Ancien montant : 50 000 FCFA
Nouveau montant : 75 000 FCFA
```

---

# 12. Base de données

Prévoir au minimum les entités suivantes :

```text
users
roles
permissions
user_permissions

schools
academic_years
academic_periods

students
guardians
student_guardians
student_enrollments

teachers
classes
class_levels
subjects
teacher_subjects
class_subjects

rooms
timetables
timetable_slots

attendance
attendance_records

assessments
grades
exams
exam_results
report_cards

fee_types
fee_structures
invoices
invoice_items
payments
payment_methods

cash_sessions
cash_transactions

income_categories
expenses
expense_categories

documents
document_templates

announcements
notifications

audit_logs

settings
```

Ajouter les clés étrangères, index, contraintes d’unicité et relations nécessaires.

Toutes les données métier doivent être correctement rattachées à l’établissement avec `school_id` lorsque nécessaire.

Les données académiques doivent être rattachées à `academic_year_id` lorsque nécessaire.

---

# 13. Architecture technique recommandée

Utiliser une architecture moderne et maintenable.

## Frontend

- Next.js
- TypeScript
- Tailwind CSS
- composants UI modernes
- interface responsive

## Backend

Choisir une architecture API propre et sécurisée.

Options possibles :

- API Next.js structurée ;
- ou NestJS pour un backend séparé.

## Base de données

- PostgreSQL
- ORM : Prisma

## Infrastructure

Prévoir :

- Docker ;
- variables d’environnement ;
- migrations ;
- sauvegardes ;
- logs ;
- CI/CD ;
- environnement développement ;
- environnement production.

---

# 14. Structure de l’application

Prévoir une structure claire :

```text
/app
/components
/modules
/lib
/services
/hooks
/types
/validators
/db
/prisma
/public
/tests
```

Chaque module métier doit être suffisamment isolé pour pouvoir évoluer indépendamment.

---

# 15. Authentification

Mettre en place :

- connexion ;
- déconnexion ;
- mot de passe sécurisé ;
- session sécurisée ;
- récupération de mot de passe ;
- protection des routes ;
- contrôle des permissions.

Le système doit identifier :

- utilisateur ;
- établissement ;
- rôle ;
- permissions.

---

# 16. Multi-tenant

Le logiciel doit être conçu pour plusieurs écoles.

Chaque école possède ses propres :

- élèves ;
- enseignants ;
- classes ;
- matières ;
- années scolaires ;
- paiements ;
- dépenses ;
- documents ;
- utilisateurs ;
- paramètres.

Aucune école ne doit pouvoir accéder aux données d’une autre école.

Le backend doit systématiquement filtrer les données par établissement.

---

# 17. Gestion des données

Ne pas supprimer définitivement les données importantes.

Utiliser des statuts :

- actif ;
- inactif ;
- archivé ;
- annulé.

Cela concerne notamment :

- élèves ;
- inscriptions ;
- paiements ;
- factures ;
- dépenses ;
- notes ;
- documents ;
- opérations financières.

---

# 18. Recherche globale

Créer une recherche globale permettant de rechercher rapidement :

- élève ;
- matricule ;
- nom ;
- prénom ;
- téléphone ;
- classe ;
- enseignant ;
- facture ;
- paiement ;
- reçu.

Depuis les résultats, l’utilisateur doit pouvoir accéder directement au dossier concerné.

---

# 19. Importation

Prévoir import :

- élèves ;
- enseignants ;
- classes ;
- matières ;
- données financières si nécessaire.

Formats :

- Excel ;
- CSV.

Avant import :

1. lire le fichier ;
2. vérifier les colonnes ;
3. vérifier les types ;
4. détecter les doublons ;
5. détecter les erreurs ;
6. afficher un rapport ;
7. permettre la confirmation ;
8. importer uniquement les données valides.

---

# 20. Exportation

Prévoir export :

- PDF ;
- Excel ;
- CSV.

Les exports doivent respecter les permissions de l’utilisateur.

---

# 21. Responsive design

## Direction

Priorité :

- ordinateur ;
- tablette.

## Secrétariat

Priorité :

- ordinateur ;
- tablette.

## Professeur

Priorité :

- téléphone ;
- tablette ;
- ordinateur.

L’interface mobile du professeur doit permettre de faire rapidement :

- appel ;
- saisie de notes ;
- consultation emploi du temps.

---

# 22. Workflow de promotion annuelle

À la fin de l’année scolaire :

1. clôturer les notes ;
2. calculer les résultats ;
3. décider du statut de chaque élève ;
4. préparer la nouvelle année ;
5. promouvoir les élèves ;
6. gérer les redoublants ;
7. gérer les transferts ;
8. gérer les abandons/exclusions ;
9. créer les nouvelles inscriptions.

Statuts possibles :

- admis ;
- redoublant ;
- transféré ;
- abandonné ;
- exclu.

Ne jamais détruire l’historique précédent.

---

# 23. Ordre d’implémentation

## Phase 1 — Architecture et fondations

Créer :

- projet ;
- architecture ;
- base PostgreSQL ;
- ORM ;
- migrations ;
- authentification ;
- système multi-tenant ;
- gestion école ;
- année scolaire ;
- structure des utilisateurs.

Objectif : avoir une base technique stable.

## Phase 2 — Utilisateurs et permissions

Créer :

- Direction ;
- Secrétariat ;
- Professeur ;
- permissions granulaires ;
- protection des routes ;
- contrôle backend.

## Phase 3 — Scolarité

Créer :

- élèves ;
- responsables ;
- enseignants ;
- classes ;
- niveaux ;
- matières ;
- inscriptions ;
- historique.

## Phase 4 — Admissions et inscriptions

Créer :

- demandes d’admission ;
- dossiers ;
- validation ;
- inscription ;
- réinscription ;
- promotion ;
- redoublement ;
- transfert.

## Phase 5 — Emploi du temps et présence

Créer :

- salles ;
- emploi du temps ;
- détection des conflits ;
- présence ;
- absences ;
- retards ;
- justificatifs.

## Phase 6 — Notes et examens

Créer :

- évaluations ;
- notes ;
- coefficients ;
- examens ;
- résultats ;
- moyennes ;
- classement ;
- appréciations ;
- bulletins.

## Phase 7 — Finance

Créer :

- frais ;
- structures tarifaires ;
- factures ;
- paiements ;
- paiements partiels ;
- reçus ;
- caisse ;
- clôture de caisse.

## Phase 8 — Comptabilité et dépenses

Créer :

- recettes ;
- dépenses ;
- catégories ;
- opérations comptables ;
- impayés ;
- rapports financiers.

## Phase 9 — Documents et communication

Créer :

- modèles de documents ;
- génération PDF ;
- attestations ;
- certificats ;
- relevés ;
- annonces ;
- notifications internes.

## Phase 10 — Rapports et outils avancés

Créer :

- tableaux de bord avancés ;
- rapports ;
- recherche globale ;
- import Excel/CSV ;
- export ;
- statistiques ;
- journal d’activité.

## Phase 11 — Tests et mise en production

Effectuer :

- tests unitaires ;
- tests d’intégration ;
- tests end-to-end ;
- tests de permissions ;
- tests multi-tenant ;
- tests financiers ;
- tests de sécurité ;
- tests de performance ;
- correction des bugs ;
- optimisation ;
- sauvegardes ;
- préparation production.

---

# 24. Règles de développement avec Antigravity

Antigravity doit travailler de manière progressive.

Pour chaque phase :

1. analyser les besoins ;
2. concevoir la structure ;
3. implémenter ;
4. créer les migrations ;
5. créer les interfaces ;
6. connecter frontend et backend ;
7. tester ;
8. corriger les erreurs ;
9. vérifier les permissions ;
10. vérifier les données ;
11. passer à la phase suivante uniquement lorsque la phase est stable.

Ne pas créer uniquement des maquettes.

Chaque fonctionnalité doit être réellement connectée à la base de données.

Ne pas utiliser de fausses données comme solution finale.

---

# 25. Tests obligatoires

Tester notamment :

### Utilisateurs

- Direction ;
- Secrétariat ;
- Professeur.

### Permissions

Vérifier qu’un professeur ne peut jamais accéder aux finances.

Vérifier qu’un secrétaire ne peut pas modifier les paramètres réservés à la Direction.

### Multi-tenant

Vérifier qu’un utilisateur d’une école ne peut jamais voir les données d’une autre école.

### Finance

Tester :

- paiement total ;
- paiement partiel ;
- paiement multiple ;
- annulation ;
- solde ;
- impayé ;
- clôture de caisse ;
- écart de caisse.

### Pédagogie

Tester :

- saisie de notes ;
- calcul des moyennes ;
- coefficients ;
- classement ;
- bulletins.

### Année scolaire

Tester :

- nouvelle année ;
- promotion ;
- redoublement ;
- historique ;
- clôture.

---

# 26. Fonctionnalités à prévoir pour les versions futures

## V2

Préparer l’architecture pour :

- SMS ;
- email ;
- WhatsApp ;
- Mobile Money ;
- notifications push ;
- application mobile professeur ;
- mode faible connexion ;
- imports avancés ;
- génération automatique d’emplois du temps ;
- statistiques avancées.

## V3

Éventuellement ajouter :

- assistant IA ;
- analyses prédictives ;
- portail parent ;
- portail élève ;
- bibliothèque ;
- transport ;
- cantine ;
- ressources pédagogiques ;
- RH ;
- paie ;
- gestion plus avancée des établissements.

Ces fonctionnalités ne doivent pas être ajoutées au MVP sans nécessité.

---

# 27. Priorités absolues

Pendant toute l’implémentation, respecter cet ordre de priorité :

1. **Stabilité**
2. **Sécurité**
3. **Intégrité des données**
4. **Simplicité d’utilisation**
5. **Performance**
6. **Évolutivité**
7. **Design**

Le logiciel doit être conçu comme un véritable produit SaaS exploitable en production, et non comme une simple démonstration.

---

# 28. Règle finale

Ne jamais ajouter de nouveaux types d’utilisateurs sans validation.

Les seuls utilisateurs sont :

- **Direction**
- **Secrétariat**
- **Professeur**

Le Secrétariat regroupe les fonctions :

- secrétaire ;
- caissier ;
- comptable.

Les élèves et les responsables/tuteurs sont des données métier, pas des utilisateurs du logiciel dans le MVP.

L’objectif est de construire progressivement un ERP scolaire complet, fiable, sécurisé, moderne et facile à utiliser.
