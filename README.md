# SAE_302_Développer_des_applications_communicantes

## Présentation du projet

Dans le cadre de la SAÉ 302, ce projet de groupe a consisté à concevoir et déployer une application avec architecture réseau **Client/Serveur** complète au-dessus de la couche de transport **UDP (port 3333)**, inspirée d'application de messageries instantanées (comme WhatsApp).

Le système que nous avons mis en place permet la gestion des comptes, l'ajout d'amis, la création de groupes de discussion avec plusieurs utilisateurs et l'échange de messages en temps réel ou asynchrone (mode boîte aux lettres en mémoire vive).

> Nous avons utilisé l'intelligence artificielle dans ce projet, cependant cela a été exclusivement fait pour concevoir et améliorer les éléments visuels et graphiques de nos applications, l'intégralité de l'architecture réseau, du protocole et de la logique applicative ayant été développée par notre groupe.

---

## Environnements de Développement & Rôles

Le développement a été articulé autour de deux IDE complémentaires, chacun ciblant un maillon clé de la chaîne de communication client/serveur :

<img width="2752" height="1536" alt="AndroidStudio-NetBeans" src="https://github.com/user-attachments/assets/7b1aafba-e45b-45e9-998f-286a4b659724" />

> **Application de réseau social/messagerie instantanée réalisé sur Netbeans et Android Studio Code**  
> Projet universitaire réalisé en BUT Réseaux & Télécommunications — IUT Belfort-Montbéliard (Université de Franche-Comté).

### 1. Apache NetBeans — Cœur Réseau & Prototype Swing
* **Présentation :** IDE modulaire de référence pour le développement Java standard (SE).
* **Rôle dans le projet :**
  * **Serveur Central UDP :** Implémentation du moteur de communication (port 3333), du stockage volatile des sessions en RAM et du parseur de commandes CSV.
  * **Banc d'essai Swing :** Conception d'un premier client graphique de bureau pour valider le protocole applicatif et exécuter des scénarios de test multi-clients sans la lourdeur d'un émulateur mobile.

### 2. Android Studio — Client Mobile Final
* **Présentation :** IDE officiel de Google dédié à la création et à l'émulation d'applications sous Android.
* **Rôle dans le projet :**
  * **Interface Mobile Moderne :** Conception d'une UI réactive à base de layouts XML et de formes vectorielles sur mesure (bulles de chat asymétriques, menu latéral *Navigation Drawer*, badges de notifications).
  * **Gestion Réseau Asynchrone :** Déport obligatoire des sockets UDP hors du *Main UI Thread* via des threads d'arrière-plan et callbacks (`UdpClient.java` / `UdpListener`) pour garantir la fluidité de l'interface.
  * **Validation & Emulation :** Tests fonctionnels complets sur périphériques virtuels (AVD) et terminaux réels.

---

## Démonstrations Vidéo

Retrouvez les présentations détaillées du fonctionnement du serveur, du client Swing et de l'application mobile :

* 📺 **Playlist YouTube complète des démonstrations :** [Visionner la playlist SAÉ 302](https://youtube.com/playlist?list=PLQInjHNJmEy8&si=s7LOKobYztM72_EY)
  * Démonstration du client et du serveur sous **Apache NetBeans**
  * Démonstration complète de l'application mobile sous **Android Studio**

---

## Équipe de projet

Le projet a été mené selon la méthode Agile avec la répartition des rôles suivante :

* **Florian Joyez** : Chef de projet & Développeur client Android Studio
* **Mohamed-Amin Barkani** : Développeur client Android Studio
* **Redouane Azmani** : Responsable serveur NetBeans & Développeur client graphique NetBeans

---

## Architecture globale & Technologies

Le projet adopte un patron d'architecture **MVC (Modèle-Vue-Contrôleur)** scindé en trois briques principales :

```text
       ┌──────────────────────┐           ┌──────────────────────┐
       │   Client Android     │           │   Client NetBeans    │
       │   (Android Studio)   │           │   (Java Swing MVC)   │
       └──────────┬───────────┘           └──────────┬───────────┘
                  │                                  │
                  │        Paquets UDP (CSV)         │
                  └──────────────► ◄─────────────────┘
                                   │
                                   ▼
                      ┌────────────────────────┐
                      │    Serveur Central     │
                      │   Java Sockets (3333)  │
                      │  (Stockage mémoire RAM)│
                      └────────────────────────┘
