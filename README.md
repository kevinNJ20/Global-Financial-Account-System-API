# Global Financial Account System API

API System pour la gestion des comptes financiers dans Global Data via Supabase.

## Description

Cette API fournit un accès standardisé aux comptes financiers, transactions et cartes dans le service Global Data. C'est la copie dorée (golden copy) des données financières.

## Endpoints

### GET /api/global/accounts
Récupère la liste des comptes globaux.

**Query Parameters:**
- `globalId` (optional): ID global du compte
- `customerGlobalId` (optional): ID global du client propriétaire
- `accountNumber` (optional): Numéro de compte
- `accountType` (optional): Type de compte
- `limit` (optional, default: 100)
- `offset` (optional, default: 0)

### POST /api/global/accounts
Upsert d'un compte financier global.

### GET /api/global/accounts/{accountGlobalId}
Récupère un compte par son Global ID (inclut les propriétaires).

### GET /api/global/accounts/transactions
Récupère les transactions globales avec filtres.

**Query Parameters:**
- `accountGlobalId` (optional): ID global du compte
- `startDate` (optional): Date de début
- `endDate` (optional): Date de fin
- `limit` (optional, default: 100)
- `offset` (optional, default: 0)

### POST /api/global/accounts/transactions
Upsert d'une transaction globale.

### GET /api/global/accounts/cards
Récupère les cartes globales.

**Query Parameters:**
- `customerGlobalId` (optional): ID global du client
- `accountGlobalId` (optional): ID global du compte
- `limit` (optional, default: 100)
- `offset` (optional, default: 0)

### POST /api/global/accounts/cards
Upsert d'une carte globale.

## Configuration

Voir README.md de Core Banking Customers System API pour la configuration de base.

### Tables Utilisées

- `global_accounts`: Comptes financiers globaux
- `global_account_owners`: Relation client-compte
- `global_transactions`: Transactions globales
- `global_cards`: Cartes globales

## Architecture Technique

### Flows Business-Logic

- `get-accounts-business-logic`: Liste des comptes avec propriétaires
- `upsert-account-business-logic`: Upsert compte avec gestion propriétaires
- `get-account-by-global-id-business-logic`: Compte par Global ID
- `get-transactions-business-logic`: Liste des transactions
- `upsert-transaction-business-logic`: Upsert transaction
- `get-cards-business-logic`: Liste des cartes
- `upsert-card-business-logic`: Upsert carte

