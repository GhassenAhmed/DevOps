# 🛒 Gestion Commerciale — Spring Boot

Une API REST de gestion commerciale développée avec **Spring Boot**, couvrant la gestion des produits, fournisseurs, factures, stocks et règlements.

---

## 📋 Table des matières

- [Fonctionnalités](#fonctionnalités)
- [Entités principales](#entités-principales)
- [Stack technique](#stack-technique)
- [Démarrage](#démarrage)
- [Configuration](#configuration)
- [Structure du projet](#structure-du-projet)
- [Endpoints API](#endpoints-api)
- [Contribuer](#contribuer)
- [Licence](#licence)

---

## ✨ Fonctionnalités

- 📦 Gestion des **produits** et de leurs catégories
- 🏭 Gestion des **fournisseurs** avec leurs détails et secteurs d'activité
- 🧾 Création et suivi des **factures** avec détails ligne par ligne
- 💰 Gestion des **règlements** (paiements)
- 📊 Suivi du **stock** en temps réel
- 👤 Gestion des **opérateurs** (utilisateurs internes)
- 🗂️ Catégorisation des fournisseurs et des produits

---

## 🗃️ Entités principales

| Entité | Description |
|---|---|
| `Produit` | Produits disponibles à la vente |
| `CategorieProduit` | Catégories des produits |
| `Fournisseur` | Fournisseurs partenaires |
| `DetailFournisseur` | Informations détaillées des fournisseurs |
| `CategorieFournisseur` | Catégories des fournisseurs |
| `SecteurActivite` | Secteurs d'activité des fournisseurs |
| `Facture` | Factures générées |
| `DetailFacture` | Lignes de détail d'une facture |
| `Reglement` | Paiements associés aux factures |
| `Stock` | Gestion des niveaux de stock |
| `Operateur` | Utilisateurs/opérateurs du système |

---

## 🛠️ Stack technique

- **Java 17+**
- **Spring Boot 3.x**
- **Spring Data JPA / Hibernate**
- **Spring Web (REST)**
- **Maven**
- **Base de données** : MySQL / PostgreSQL (configurable)
- **Lombok** (recommandé)

---

## 🚀 Démarrage

### Prérequis

- Java 17+
- Maven 3.8+
- MySQL ou PostgreSQL installé et en cours d'exécution

### Installation

```bash
# Cloner le dépôt
git clone https://github.com/ton-utilisateur/gestion-commerciale.git
cd gestion-commerciale

# Compiler le projet
mvn clean install

# Lancer l'application
mvn spring-boot:run
```

L'API sera disponible sur : `http://localhost:8080`

---

## ⚙️ Configuration

Modifie le fichier `src/main/resources/application.properties` :

```properties
# Base de données
spring.datasource.url=jdbc:mysql://localhost:3306/gestion_commerciale
spring.datasource.username=root
spring.datasource.password=ton_mot_de_passe
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA / Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# Port du serveur
server.port=8080
```

---

## 📁 Structure du projet

```
src/
└── main/
    ├── java/
    │   └── com/exemple/gestioncommerciale/
    │       ├── entities/
    │       │   ├── Produit.java
    │       │   ├── CategorieProduit.java
    │       │   ├── Fournisseur.java
    │       │   ├── DetailFournisseur.java
    │       │   ├── CategorieFournisseur.java
    │       │   ├── SecteurActivite.java
    │       │   ├── Facture.java
    │       │   ├── DetailFacture.java
    │       │   ├── Reglement.java
    │       │   ├── Stock.java
    │       │   └── Operateur.java
    │       ├── repositories/
    │       ├── services/
    │       ├── controllers/
    │       └── GestionCommercialeApplication.java
    └── resources/
        └── application.properties
```

---

## 📡 Endpoints API

### Produits
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/produits` | Lister tous les produits |
| `GET` | `/api/produits/{id}` | Obtenir un produit |
| `POST` | `/api/produits` | Créer un produit |
| `PUT` | `/api/produits/{id}` | Modifier un produit |
| `DELETE` | `/api/produits/{id}` | Supprimer un produit |

### Fournisseurs
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/fournisseurs` | Lister tous les fournisseurs |
| `GET` | `/api/fournisseurs/{id}` | Obtenir un fournisseur |
| `POST` | `/api/fournisseurs` | Créer un fournisseur |
| `PUT` | `/api/fournisseurs/{id}` | Modifier un fournisseur |
| `DELETE` | `/api/fournisseurs/{id}` | Supprimer un fournisseur |

### Factures
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/factures` | Lister toutes les factures |
| `GET` | `/api/factures/{id}` | Obtenir une facture |
| `POST` | `/api/factures` | Créer une facture |
| `PUT` | `/api/factures/{id}` | Modifier une facture |
| `DELETE` | `/api/factures/{id}` | Supprimer une facture |

### Stock
| Méthode | Endpoint | Description |
|---|---|---|
| `GET` | `/api/stocks` | Voir l'état du stock |
| `PUT` | `/api/stocks/{id}` | Mettre à jour le stock |

---

## 🤝 Contribuer

Les contributions sont les bienvenues !

1. Fork le projet
2. Crée une branche (`git checkout -b feature/ma-fonctionnalite`)
3. Commit tes changements (`git commit -m 'Ajout de ma fonctionnalité'`)
4. Push la branche (`git push origin feature/ma-fonctionnalite`)
5. Ouvre une Pull Request

---

## 📄 Licence

Ce projet est sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
