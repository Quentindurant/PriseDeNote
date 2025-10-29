
## 1. Contexte et objectifs
L’outil CRM **SYNAPSE** vise à centraliser l’ensemble des activités de support, déploiement, ADV et comptabilité dans un environnement unique, modulable et adapté aux besoins spécifiques de l’entreprise (entre partenaires et clients).

**Différences avec un CRM du marché (Zoho, Hubspot, etc.) :**
- Adaptation à nos process spécifiques (ADV + staging matériel + partenaires + interventions terrain).
- Vue partenaire/clients/techniciens croisée, impossible avec un CRM générique.
- Interface simplifiée et intuitive pour les rôles métiers (pas de menus génériques surchargés).
- Planification techniciens + interventions intégrée au cœur du CRM.

---

## 2. Utilisateurs & Rôles
👉 Chaque rôle a des permissions précises (CRUD + validation).

- **Admin** : vision globale, gestion des utilisateurs, partenaires, techniciens, rapports, logs, sécurité.  
- **Support** : tickets (création, suivi, clôture/escalade).  
- **Staging** : préparation matériel (stock, provisioning), suivi commandes.  
- **ADV** : cycle complet devis → commande → livraison → planification → gestion des techniciens.  
- **Compta** : factures, paiements, relances, reporting CA/marge.  
- **Techniciens internes/externes** : interventions terrain, PV signés, disponibilités.  
- **Chefs de projet** : supervision interventions/projets, suivi qualité.  
- **Partenaires** : accès restreint → leurs clients, tickets, commandes.  

---

## 3. Modules fonctionnels

### Gestion des clients
- Fiche client : coordonnées, SIRET/TVA, contacts, notes internes.  
- Lien avec partenaire si le client vient d’un distributeur.  
- Historique complet : interventions, tickets, commandes, factures.  
- Segmentation : secteur, taille, type (pharmacie, assurance, etc.).  

### Tickets (Support)
- Création par support ou par partenaire.  
- Typologie : incident / demande / projet / SAV.  
- Statuts : ouvert, en cours, en attente client, résolu, clos, escaladé.  
- SLA : délais de traitement & alertes.  
- Attribution auto ou manuelle à un technicien interne/externe.  
- Recherche intelligente client (par numéro, nom, système).  
- Historique du ticket (traçabilité via journal).  

### Commandes (ADV)
- Cycle complet : saisie → validation ADV → staging → expédition → installation → facturation.  
- Produits/services : catalogue (prix, coûts, TVA).  
- Notifications mail auto client aux étapes clés.  
- Lien direct commandes → factures.  
- Gestion des statuts (en attente, en préparation, livré, annulé).  

### Techniciens
- Coordonnées, compétences, zones couvertes.  
- Disponibilités et plannings (intégration congés, absences).  
- Géolocalisation (option).  
- Notation (ponctualité, qualité, efficacité).  
- Rattachement à interventions/tickets.  

### Planning & Carte interactive
- Vue calendrier (jour/semaine/mois) des interventions.  
- Carte France : techniciens positionnés + clients actifs + tickets ouverts.  
- Filtrage par technicien, statut, zone.  
- Gestion des conflits de planning.  

### Interventions
- Création à partir d’un ticket/commande.  
- Dates/heures + technicien(s) assignés.  
- PV signé (client) + notes interne technicien + photos/documents.  
- Checklists (contrôles qualité).  

### Communication & Notifications
- Emails automatiques (commandes, tickets, interventions, factures).  
- SMS de rappel (RDV, relance).  
- Notifications internes : retard, escalade, dépassement SLA.  

### Compta
- Factures automatiques (basées sur commandes).  
- Suivi paiements (statut payé, partiel, en attente).  
- Relances automatiques par mail.  
- Tableaux de bord : CA, marges, impayés.  
- Rattachement factures → paiements (rapprochement simple).  

### ADV
- Gestion devis/commandes (quotes → orders).  
- Staging matériel (préparation, provisioning, stock).  
- Suivi livraisons (transporteur, tracking).  
- Planification techniciens (emplois du temps, créneaux, rappels).  
- Documents : devis, BC, BL, PV signé, facture/avoir (générés en PDF).  
- Notifications clients (mail/SMS) aux étapes clés.  

---

## 4. Modules transverses
- Recherche globale : clients, tickets, commandes, techniciens.  
- Dashboard/statistiques : adaptés par rôle (support = tickets SLA, ADV = commandes/factures, Compta = CA/marge).  
- RGPD & sécurité : logs actions, droits d’accès fins, cryptage mots de passe.  
- Mobile friendly : interface techniciens (planning, signature PV, documents).  
- Audit logs : actions, connexions, IP, sessions.  

---

## 5. Suggestions évolutives 💡
- Gestion de stocks (matériel staging).  
- Chat interne (type Slack simplifié).  
- Suivi contrats de maintenance (dates, alertes, SLA).  
- IA de pré-support : classification tickets, suggestions de résolution.  
- Module marketing (campagnes, leads, opportunités, suivi conversion).  

---

## Tableau des droits simplifié

| Module         | Admin | Support | Commercial | ADV | Tech Interne | Tech Terrain | Chef Projet | Compta | Partenaire         |
|----------------|-------|---------|------------|-----|--------------|--------------|-------------|--------|--------------------|
| Clients        | ✅    | 👁️      | ✅          | ✅  | 👁️           | 👁️           | 👁️          | 👁️     | ✅ Ses clients      |
| Tickets        | ✅    | ✅       | 👁️          | 👁️  | ✅            | ✅            | 👁️          | ❌      | ✅ Ses tickets      |
| Commandes      | ✅    | 👁️      | ✅          | ✅  | 👁️           | 👁️           | 👁️          | 👁️     | ✅ Ses commandes    |
| Planning       | ✅    | ❌       | 👁️          | ✅  | 👁️           | ✅ Personnel  | ✅          | ❌      | 👁️ Ses interventions |
| Interventions  | ✅    | ❌       | 👁️          | ✅  | ✅ Support    | ✅ Terrain    | ✅          | ❌      | 👁️ Chez ses clients |
| Staging/Stock  | ✅    | ❌       | ❌          | ✅  | ✅            | ❌            | 👁️          | ❌      | ❌                 |
| Comptabilité   | ✅    | ❌       | ❌          | ❌  | ❌            | ❌            | ❌          | ✅      | ❌                 |

---

## TECHNOLOGIES
- **Nest.JS (Framework JS relationnel à la BDD)  
- **React + Next.JS / React Native** (UX, UI)  
- **PostgreSQL** (BDD)  

---

## DELAI
- Priorité aux modules **ADV, Commande et Clients**  
- **V1 estimée à Mars 2026**
