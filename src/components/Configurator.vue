<template>
  <div class="configurator">
    <config-choice
       v-for="choice in this.choices"
       :key="choice.id"
       :choice="choice"
       @choosen="choosen"
     />
  </div>
</template>

<style lang="sass">
@import "../../node_modules/bulma/bulma.sass";
</style>

<script>
import _ from 'lodash'
import axios from 'axios'
import Choice from './Choice'

export default {
  name: 'configurator',

  components: {
    'config-choice': Choice
  },

  mounted () {
    axios.get('http://localhost:8002/').then(response => {
      this.choices = response.data
    })
  },

  data () {
    return {
      choices: []
    }
  },

  methods: {
    choosen (id) {
      _.each(this.choices, (x) => {
        if (x.id === id) {
          x.selected = true
          return false
        }
      })

      this.openNext(id)
    },
    openNext (id) {
      let next = 0
      _.each(this.choices, (x) => {
        if (next === 1) {
          x.open = true
          next = 2
        } else if (next === 2) {
          x.open = false
          x.selected = false
        }

        if (x.id === id) {
          next = 1
        }
      })
    }
  }
}
</script>
