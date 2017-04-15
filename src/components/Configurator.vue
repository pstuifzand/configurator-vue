<template>
  <div class="configurator">
    <config-choice
       v-for="choice in this.choices"
       :key="choice.id"
       :choice="choice"
       @choosen="choosen"
     />

    <config-result :value="this.calculation" />
  </div>

</template>

<style lang="sass">
@import "../../node_modules/bulma/bulma.sass";
</style>

<script>
import _ from 'lodash'
import axios from 'axios'
import Choice from './Choice'
import Calculation from './Calculation'

export default {
  name: 'configurator',

  components: {
    'config-choice': Choice,
    'config-result': Calculation
  },

  mounted () {
    this.reloadChoices()
  },

  data () {
    return {
      choices: [],
      params: {},
      calculation: []
    }
  },

  methods: {
    reloadChoices () {
      let params = this.params
      axios.get('http://localhost:8002/', { 'params': params }).then(response => {
        this.choices = response.data.choices
        this.calculation = response.data.result
      })
    },

    choosen (choiceId, optionId) {
      this.params['choice[' + choiceId + ']'] = optionId

      _.each(this.choices, (x) => {
        if (x.id === choiceId) {
          x.selected = true
          return false
        }
      })

      this.reloadChoices()
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
