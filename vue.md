---
description: Wat is Vue.js/Nuxt
---

# Vue.js

Voor de eerste opdracht heb ik met Vue.js/Nuxt en met Buefy gewerkt, dit zijn frameworks voor Javascript en Css. Met deze opdracht heb ik de basis concepten van een framework leren kennen en leren me om te gaan. Deze concepten zijn.

* Data mutation
* Data actions
* States
* Templating
* Vue one page

#### Data actions:

Data action heb je nodig om de data mutations aan te roepen je kan deze hergebruiken maar er mag geen logica inzitten.

```javascript
 updateData(context, updatedData){
    context.commit('updatedData',updatedData)
  },
```

#### Data mutation:

Data mutations zijn de Vue manier om je state aan te passen als je ook maar iets will aanpassen in de state moet dat via deze ketting van functions.

```javascript
export const mutations = {
  toggleShow (state, toggle) {
    state.popUp.isOpen = toggle
  },
```

#### State update:

Hier is de state van de app, dit is data die aan elke page meegegeven kan worden.

```javascript
export const state = () => ({
  popUp: {
    isOpen: false,
    item: '',
    name: '',
    parents: ''
  },
  jsonData: {},
  logBook:{
    hasStorage: false
  },
  mainUrl:'',
  partUrl:{},
})

```

#### Templating:

Vue templating werkt eigelijk het zelfde als veel anderen templating. In Vue de Javascript, HTML en Css is in het zelfde bestand en wordt door Vue zelf in elkaar gezet tot correcten bestanden. Data doorgeven en dynamic data updates is Vue.js zijn ding als je de elementen uit Vue correct gebruikt krijg je dynamic data update over de site en of app.

Vue heeft ook zijn eigen "Html" tags gemaakt zo als een `v-model` dit model maakt een door Vue gelinked element wat automatics data update.

Vue heeft ook zijn eigen Javascript methods gemaakt `@click=""` is dus gewoon een `onclick=""` maar dan dynamisch door Vue.

```markup
<div class="modal-update-holder">
  <p>{{popUpData.name}}:</p>
  <input type="text" v-model="isValue">
  <button @click="updatedData" class="button is-medium is-primary">Update data</button>
</div>
```

