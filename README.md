# pnf-portfolio

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

## FontAwesome

In order to use fontAwesome in project we should do Following steps

1. to add new Icon we should go in -> nuxt.config.js and in fontAwesome section we have to add icons name in the right Category [solid ,regular ,brand]

// nuxt.config.js
fontawesome: {
component: "fa",
icons: {
solid: ['faEnvelope', 'faCog'],
brands: true,
regular: true
}
},

index.vue

  <template>
   <fa  :icon="['fas','anchor']" />
  </template>

//
or If we want to add in our component.vue File do this

import { fas } from '@fortawesome/free-solid-svg-icons'
import { faGithub } from '@fortawesome/free-brands-svg-icons'

export default {
computed: {
fas () {
return fas // NOT RECOMMENDED
},
faGithub () {
return faGithub
}
},
}

      <fa :icon="fas.faAddressBook"  />
        <fa :icon="faGithub" />
