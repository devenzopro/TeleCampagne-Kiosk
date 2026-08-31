# Changelog

Toutes les modifications notables de ce projet seront documentées dans ce fichier.

Le format est basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/)
et ce projet adhère à la gestion sémantique de version [Semantic Versioning](https://semver.org/lang/fr/).

## [1.0.0] - 2026-08-31

### Ajouté
- Architecture multi-réseaux isolée sous Docker (`Clients`, `DMZ`, `Admin`).
- API REST Node.js pour l'assignation dynamique des URLs par adresse MAC / UUID.
- Deux conteneurs pare-feu avec filtrage strict et NAT `iptables`.
- Script de bootstrap automatique (`bootstrap.sh`) pour clients Ubuntu / Raspberry Pi.
- Client d'administration Python pour la gestion du parc.
