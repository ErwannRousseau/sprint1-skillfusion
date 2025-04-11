---
background: /assets/atelier.png
theme: seriph
title: SkillFusion
description: Présentation du Sprint 1
class: lead
transition: slide-left
---

# Projet SkillFusion

### Présentation du Sprint 1

**Équipe :** Julien, Mickael, Erwann, Leonard

---
layout: two-cols
---

## Contexte du projet

SkillFusion est une plateforme de tutoriels DIY (bricolage) :

- Apprentissage à distance, à son rythme
- Articles illustrés, cas pratiques
- Forum pour entraide entre utilisateurs
- Dashboard pour apprenants et instructeurs

🎯 Objectif : Proposer un MVP fonctionnel et qui laisse place a une evolution

::right::

<div grid place-items-center w-full h-full>
<img src="/assets/logo.svg" size-80/>
</div>

---
layout: two-cols
---

## Sprint 1 - Ce qui était prévu

🔧 Bootstrap technique :

- Setup du projet (frontend & backend)
- Docker + Docker Compose
- CI/CD avec GitHub Actions

🖥 Pages principales :

- Home page
- Inscription
- Connexion

::right::

<div mt-12>
👨‍🎨 CRUD :

- User
- Course
- Category

🧙‍♂️ Logic authentification backend :

- JWT (signup et login)
</div>

---

## Ce qui a été fait ✅

🎉 Tout ce qui était prévu a été réalisé !

- Conteneurisation de nos services avec Docker
- Pipeline CI fonctionnelle pour le frontend
- Setup Eslint et Jest pour le frontend
- Pages fonctionnelles (home, login, register)
- Backend opérationnel (Nest.js + Prisma + PostgreSQL)
- CRUD opérationnel (user, course, category)

---

# Readme

### Prerequisites

- Docker
- Docker Compose
- Make (optional, but recommended)

### Installation

##### With Make (recommended)

You can bootstrap the entire project with a single command:

```bash
make bootstrap
```

Without Make, you can run the following commands:

```bash
cp .env.dev.dist .env
docker compose build
docker compose run --rm frontend yarn install
docker compose run --rm backend yarn install
docker compose up -d
```

---
layout: iframe
# the web page source
url: http://localhost:3000
---

<!--
La demo:

- Cloné le repo dans un nouveau dossier

- je suis le Readme, container ce lance

- Présentation de la Home
- Inscription
- Login
-->

---

## Ce qui reste à faire 🛠️

🔁 Améliorations visuelles et techniques :

- Toasts de feedback (succès/erreur)
- Loaders (états de chargement inscription/login)
- Eslint + CI pour le backend
- Améliorer la CI pour le frontend

📌 Points ajoutés à la backlog — on reste focus sur le MVP !

---
layout: two-cols
---

## Une problématique rencontrée 🤯

🖥️ Problèmes d’environnement :

- Sous Windows, pas de hot reload
- Rebuild à chaque changement

🔐 Authentification (Signup) avec Next.js :

- Problème de config `SERVER_API_URL` (3000 vs 3001), mauvais port avec Docker
- Gestion des cookies et de la redirection

✅ Solutions :

- Windows : Utilisation de WSL
- Modification de l’URL backend

::right::

<v-click>
Solutions pour la redirection (+1h):
</v-click>

<v-click>

Erreur :
```bash
NEXT_REDIRECT
```
</v-click>

<v-click>

````md magic-move
//step 1


```ts {*|13}
export async function registerAction(
  _prevState: RegisterFormState,
  data: FormData,
): Promise<RegisterFormState> {
  // ...

  try {
    // ...

    const result: RegisterUserResult = await response.json();

    await createSession(result);
    redirect("/");
  } catch (error) {
    // ...
  }
}
```

// step 2

```ts {16|*}
export async function registerAction(
  _prevState: RegisterFormState,
  data: FormData,
): Promise<RegisterFormState> {
  // ...

  try {
    // ...

    const result: RegisterUserResult = await response.json();

    await createSession(result);
  } catch (error) {
    // ...
  }
  redirect("/");
}
```
````

</v-click>

---

## Prochain sprint 🔜

📅 Sprint Planning le lundi matin

Prochaines priorités envisagées :

- Dashboard utilisateurs et instructeurs
- Édition d'un cours
- Page de détail d’un cours
- Forum (lecture, création de posts)

🧠 On définira ensemble les user stories à attaquer

---

## Merci 🙏

Des questions ? 💬
