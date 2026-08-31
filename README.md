# TeleCampagne-Kiosk

**TeleCampagne-Kiosk** est une infrastructure conteneurisée prête à l'emploi permettant de déployer et piloter un réseau d'écrans et de télévisions d'affichage (mairies, commerces de village, entreprises, associations) via une architecture réseau étanche et sécurisée.

---

## Le Concept

Le projet permet d'équiper des téléviseurs ou des écrans d'affichage basse consommation (Raspberry Pi, mini-PC) sans aucune configuration complexe sur le terrain :
1. Vous branchez l'écran sur le réseau local.
2. Le système s'initialise automatiquement (**Zero-Touch Bootstrap**).
3. L'API centrale en DMZ assigne la page web d'information locale dédiée en fonction du boîtier.
4. L'administrateur gère l'ensemble du parc via un utilitaire Python sécurisé.

---

## 🔒 Architecture de Sécurité & Réseau

```text
 [ ÉCRANS / TÉLÉS CAMPAGNE ] (172.20.10.0/24)
              │
              ▼ (Bail DHCP + Extraction URL)
      ┌──────────────┐
      │  FIREWALL 1  │ (NAT / Filtrage strict)
      └──────┬───────┘
             │
      [ DMZ SERVICES ] (172.20.20.0/24)
             ├── API REST & Inventaire (Node.js/SQLite :8080)
             ├── Serveur DHCP & DNS local
             └── Proxy HTTPS sortant filtré (Liste blanche)
             │
      ┌──────┴───────┐
      │  FIREWALL 2  │ (Fail2ban + Blocage brute-force)
      └──────┬───────┘
             ▲
             │ (Connexion sécurisée par Token)
  [ RÉSEAU ADMIN / MAIRIE ] (172.20.30.0/24)
        └── Client de gestion Python
