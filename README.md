# SAE_302_Développer_des_applications_communicantes

<img width="2752" height="1536" alt="AndroidStudio-NetBeans" src="https://github.com/user-attachments/assets/7b1aafba-e45b-45e9-998f-286a4b659724" />

> **Application de réseau social et messagerie instantanée (Amis & Groupes)**[cite: 3]  
> Projet universitaire réalisé en BUT Réseaux & Télécommunications — IUT Belfort-Montbéliard (Université de Franche-Comté)[cite: 38].

---

## 📌 Présentation du projet

Dans le cadre de la SAÉ 302, ce projet consiste à concevoir et implémenter une architecture réseau **Client/Serveur** complète au-dessus de la couche de transport **UDP (port 3333)**, inspirée du modèle des messageries instantanées de type WhatsApp[cite: 3, 4, 33].

Le système permet la gestion des comptes, l'ajout d'amis, la création de salons de discussion multi-utilisateurs et l'échange de messages en temps réel ou asynchrone (mode boîte aux lettres en mémoire vive)[cite: 3, 33].

> **Note sur l'utilisation de l'IA :** L'intelligence artificielle a été utilisée exclusivement pour concevoir et améliorer les éléments visuels et graphiques de nos applications, l'intégralité de l'architecture réseau, du protocole et de la logique applicative ayant été développée par l'équipe[cite: 48].

---

## 🎥 Démonstrations Vidéo

Retrouvez les présentations détaillées du fonctionnement du serveur, du client Swing et de l'application mobile :

* 📺 **Playlist YouTube complète des démonstrations :** [Visionner la playlist SAÉ 302](https://youtube.com/playlist?list=PLQInjHNJmEy8&si=s7LOKobYztM72_EY)
  * Démonstration du client et du serveur sous **Apache NetBeans**
  * Démonstration complète de l'application mobile sous **Android Studio**

---

## 👥 Équipe de projet

Le projet a été mené selon la méthode Agile avec la répartition des rôles suivante[cite: 41] :

* **Florian Joyez** : Chef de projet & Développeur client Android Studio[cite: 3]
* **Mohamed-Amin Barkani** : Développeur client Android Studio[cite: 3]
* **Redouane Azmani** : Responsable serveur NetBeans & Développeur client graphique NetBeans[cite: 3]

---

## 🧱 Architecture globale & Technologies

Le projet adopte un patron d'architecture **MVC (Modèle-Vue-Contrôleur)** scindé en trois briques principales[cite: 3, 12, 40] :

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
