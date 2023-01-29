---
title: Accéder à l'état d'un formulaire incontrôlé
layout: post
sitemap: true
type: article
description: Les formulaires incontrôlés sont souvent plus courts et plus lisibles. Cependant, accéder à une valeur individuelle peut être utile.
---

Les formulaires contrôlés sont pratiques car ils offrent un contrôle fin sur les différents états. Cependant, ils peuvent être un peu verbeux.

D'un autre côté, les formulaires incontrôlés sont souvent plus courts et plus lisibles. Ils se basent sur le comportement natif des éléments HTML, réduisant ainsi les tâches répétitives pour la gestion des composants contrôlés.

<div class="alert alert-block alert-info">
  An english version of this article exists on [dev.to](https://dev.to/thhareau/accessing-current-form-state-using-uncontrolled-components-51lj) 
</div>

### Formulaire contrôlé

Prenons par exemple ce formulaire. Nous avons quatre entrées, "diet" étant désactivé si la checkbox "presence" n'est pas cochée.

<iframe height="300" style="width: 100%;" scrolling="no" title="Controlled form" src="https://codepen.io/ThHareau/embed/MWBBoKj?default-tab=js%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/ThHareau/pen/MWBBoKj">
  Controlled form</a> by ThHareau (<a href="https://codepen.io/ThHareau">@ThHareau</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

Ici, nous devons gérer manuellement tous les champs. Cela fonctionne, mais semble inutile lorsque HTM``L se charge parfaitement bien de cela.

### Formulaire incontrôlé

Prenons le même exemple en utilisant un formulaire incontrôlé.

```jsx
const action = (event) => {
  event.preventDefault();

  const data = new FormData(event.currentTarget);
  console.log("Saving...", Object.fromEntries(data.entries()));
};

const App = () => {
  return (
    <div className="App">
      <form onSubmit={action}>
        <fieldset>
          <legend>Identity</legend>
          <div>
            <label for="name">Name : </label>
            <input id="name" name="name" defaultValue="Chris" />
          </div>
          <div>
            <label for="email">Email : </label>
            <input id="email" type="email" name="email" defaultValue="chris@email.test" />
          </div>
        </fieldset>

        <fieldset>
          <legend>Event</legend>
          <div>
            <label for="presence">Presence : </label>
            <input id="presence" type="checkbox" name="presence" defaultChecked />
          </div>
          <div>
            <label for="diet">Diet : </label>
            <input id="diet" name="diet" />
          </div>
        </fieldset>

        <button type="submit">Submit</button>
      </form>
    </div>
  );
};
```

Ici, nous pouvons remarquer deux changements principaux:

1. Moins de logique (et donc moins de bugs). Nous n'avons pas besoin des valeurs du formulaire avant l'action de soumission, alors pourquoi les stocker?
2. `action` lit les valeurs directement à partir de l'événement. Comme il n'utilise pas les états React, nous pouvons l'extraire en dehors du composant et découper notre code plus facilement.

Oh, et peut-être un dernier point: nous ne gérons plus le champ désactivé. Réglons cela !

### Accéder à l'état avec des formulaires incontrôlés

Nous devons lire la valeur actuelle de la checkbox "presence" pour désactiver le champ "diet". En utilisant des composants contrôlés, c'est facile. Ici, moins.

Une solution à ce problème est d'ajouter un listener onChange sur le formulaire lui-même. Il fournira un accès en lecture seule aux valeurs actuelles du formulaire.

```jsx
const App = () => {
  const [formData, setFormData] = useState(new FormData())

  return (
    <div className="App">
      <form onSubmit={action} onChange={(event) => setFormData(new FormData(event.currentTarget))}>
```


Puis, sur le champ "diet", nous ajoutons:

```jsx
<div>
  <label for="diet">Diet : </label> 
  <input
    id="diet"
    name="diet"
    disabled={formData.get("presence") !== "on"}
  />
</div>
```

Ce qui donne ce résultat final:

<iframe height="300" style="width: 100%;" scrolling="no" title="Uncontrolled form" src="https://codepen.io/ThHareau/embed/vYaaJaX?default-tab=js%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/ThHareau/pen/vYaaJaX">
  Uncontrolled form</a> by ThHareau (<a href="https://codepen.io/ThHareau">@ThHareau</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
