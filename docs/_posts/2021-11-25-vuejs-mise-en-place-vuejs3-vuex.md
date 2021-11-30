---
layout: post
title: "Mise en place d'un projet VueJS 3 en typescript"
---
# Mise en place d'un projet VueJS 3 en typescript
## Vérification des prérequis
Vérifier dans une invite de commande la présence des prérequis pour l'installation.
```cmd
node --version
npm --version
vue --version
```

Le projet est réalisé en Vuejs 3.

## Création du projet
Création du projet Weather Shield (wesh) via le client vue.
```cmd
vue create wesh
```
Choix d'une configuration manuelle avec les options ci-dessous (utiliser l'interface de commande pour la sélection):
* Vuejs 3.x
* Typescript
* Babel
* Router
* Vuex
* Linter : ESLint + Prettier
* Unit Testing : Jest
Le processus de création devrait se dérouler sans erreur. A l'issue :
```cmd
cd wesh
npm run serve
```
L"application créée est accessible via http://localhost:8080/

## Bilan de l'étape de mise en place
La mise en place d'un projet est donc complétement automatisée. Evidemment, à cet instant, il n'y a que du contenu de démo, mais il y a déjà pas mal de choses.

Le projet est **initialisé**. La structure de fichier du projet est en place.
```cmd
public/        # ressources publiques du projet déployées telles quelles
src/
├─ assets/     # ressources pour le projet vue (ex: images) packagées lors du build
├─ components/ # dossiers contenant les composants vue
├─ router/
|  └─ index.ts # fichier définissant la navigation du site (cf. ci-dessous)
├─ store/      # dossier pour la configuration du store VueX (on y reviendra)
├─ views/      # pages de l'application (utilisant les composants)
└─ App.vue     # fichier principal instanciant l'application Vue
tests/
└─ units/      # dossier pour les tests unitaires (Jest dans notre cas)
```
Personnellement, je rajoute un répertoire `src/services` pour les définitions et les appels vers API externes. 

Le projet est **opérationnel**. 3 cibles de compilation sont définies dans le fichier `package.json`. *serve* que l'on a lancé précedemment est qui permet de lancer locallement l'application, *build* qui permet le packaging de l'application en vue de son déploiement sur un environnement cible, *test:unit* qui lance les tests unitaires et *lint* qui controlle les règles de règle de codage.
```md
> npm run build
-  Building for production...

 DONE  Compiled successfully in 4343ms

  dist\js\chunk-vendors.e7def1a6.js    153.71 KiB   54.64 KiB
  dist\js\app.53cb775b.js              5.26 KiB     2.26 KiB
  dist\js\about.46d83841.js            0.38 KiB     0.29 KiB
  dist\css\app.534b304f.css            0.25 KiB     0.19 KiB

  Images and other types of assets omitted.

 DONE  Build complete. The dist directory is ready to be deployed.

```

L'application est **fonctionnelle**. Elle donne un exemple d'une application possédant 2 pages "Home" et "About". Le fichier `router\index.ts` est en place,prêt à être modifié pour le projet cible. 
```typescript
const routes: Array<RouteRecordRaw> = [
  {
    path: "/",
    name: "Home",
    component: Home,
  },
  {
    path: "/about",
    name: "About",
    // route level code-splitting
    // this generates a separate chunk (about.[hash].js) for this route
    // which is lazy-loaded when the route is visited.
    component: () =>
      import(/* webpackChunkName: "about" */ "../views/About.vue"),
  },
];
```
Chaque route est une entrée du tableau `routes`, l'exemple donné illustre aussi le *lazy loading* qui permet si on le souhaite de ne charger les codes javascript qu'au moment de la navigation vers la page. Dans les applications de plus grande taille, cela est une façon de compartimenter son code pour accélerer le rendu des pages dans le navigateur.

Le fichier `src/views/Home.vue` donne une illustration de l'approche par composant de Vuejs :
```typescript
<template>
  <div class="home">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue";

@Options({
  components: {
    HelloWorld
  },
})
export default class Home extends Vue {}
</script>
```
Dans le bloc *\<template\>*, il y a le code "html" du composant, on y voit une balise classique *img* pour l'affichage d'une image et l'utilisation d'une balise moins classique *HelloWorld* avec un attribut *msg*, permettant l'instanciation du composant Vue ``src/components/HelloWorld.vue``. Le bloc *\<script\>* contient le code typescript permettant l'inclusion du composant. Ce sera plus parlant avec l'exmple du composant ``src/components/HelloWorld.vue`` ci-dessous.
```typescript
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    ...
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    msg: String,
  },
})
export default class HelloWorld extends Vue {
  msg!: string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
...
</style>

```
Ce composant simple prend en entrée (une propriété ou *props*) une chaine de charactères *msg* et l'affiche sous forme de balise *h1* sur la page. On voit ici la structure d'un fichier Vue "single file", blocs *html*, *script* et *style*, ainsi que la syntaxe `{{ msg }}` dans le bloc *html* pour accéder à la valeur de la propriété.

L'application est **testée**. Le composant de démo `HelloWorld.vue` vient avec son script de test unitaire.

```md
> npm run test:unit
PASS  tests/unit/example.spec.ts
  HelloWorld.vue
    √ renders props.msg when passed (28ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        2.948s, estimated 5s
Ran all test suites.
```

On a ainsi de manière quasi immédiate un environnement prêt à l'emploi, initialisé et opérationnel, et une base d'application fonctionnelle et testée. 

Il n'y a plus qu'à !
