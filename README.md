# Scenium - Landing Page

Scenium est une plateforme de réservation de scènes événementielles mobiles. Ce projet est une landing page interactive conçue avec **Next.js** pour présenter nos solutions de scènes uniques ("Fleur", "Nuage", "Ballon") et permettre la prise de contact et la réservation simplifiée.

## 🚀 Technologies

- **Framework** : [Next.js](https://nextjs.org/) (App Router)
- **Langage** : TypeScript
- **Animations** : GSAP
- **Stylisation** : Tailwind CSS
- **Tests** : Vitest + React Testing Library
- **Conteneurisation** : Docker

---

## 🛠️ Installation et Lancement (Local)

1. **Installer les dépendances** :
   ```bash
   npm install
   ```

2. **Lancer le serveur de développement** :
   ```bash
   npm run dev
   ```
   Accédez à [http://localhost:3000](http://localhost:3000).

---

## 🐳 Lancement avec Docker

Le projet inclut une configuration Docker pour le développement :

1. **Lancer l'environnement de développement** :
   ```bash
   docker-compose up --build
   ```
   L'application sera accessible sur le port **3000** avec le rechargement à chaud (Hot Reload) activé via les volumes.

---

## 🧪 Tests

Nous utilisons **Vitest** pour garantir la stabilité du projet, notamment pour le formulaire de contact.

1. **Lancer les tests** :
   ```bash
   npm test
   ```

> [!NOTE]
> Un workflow **GitHub Actions** (CI) est configuré pour exécuter automatiquement ces tests à chaque push sur la branche `main`.

---

## 📦 Build et Production

Pour générer une version optimisée du projet :

```bash
npm run build
```
Le projet est prêt à être déployé.
