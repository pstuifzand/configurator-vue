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
import Choice from './Choice'

export default {
  name: 'configurator',

  components: {
    'config-choice': Choice
  },

  data () {
    return {
      choices: [
        {
          id: 1,
          title: 'Kies je productiemethode',
          name: 'production',
          open: true,
          selected: false,
          type: 'radio',
          options: [
            { title: 'Digitaal', id: 1 },
            { title: 'Offset', id: 2 }
          ]
        },
        {
          id: 2,
          title: 'Kies het eindformaat',
          name: 'size',
          open: false,
          selected: false,
          type: 'radio',
          options: [
            { title: 'A4', id: 1 },
            { title: 'A5', id: 2 },
            { title: 'A6', id: 3 },
            { title: 'Lang A5', id: 4 },
            { title: 'Vierkant (210mm x 210mm)', id: 5 },
            { title: 'Vierkant (135mm x 135mm)', id: 6 }
          ]
        },
        {
          id: 3,
          title: 'Kies de vouwrichting',
          name: 'size',
          open: false,
          selected: false,
          type: 'radio',
          options: [
            { title: 'Staand', id: 1 },
            { title: 'Liggend', id: 1 }
          ]
        },
        {
          id: 4,
          title: 'Aantal pagina\'s inclusief omslag',
          name: 'page_count',
          open: false,
          selected: false,
          type: 'select',
          options: [
            { title: '8 Pagina\'s', id: 1 },
            { title: '12 Pagina\'s', id: 2 },
            { title: '16 Pagina\'s', id: 3 },
            { title: '20 Pagina\'s', id: 4 },
            { title: '24 Pagina\'s', id: 5 },
            { title: '28 Pagina\'s', id: 6 }
          ]
        },
        {
          id: 5,
          title: 'Kies de oplage',
          name: 'size',
          open: false,
          selected: false,
          type: 'radio',
          options: [
            { title: '100', id: 1 },
            { title: '250', id: 2 },
            { title: '500', id: 3 },
            { title: '1000', id: 4 },
            { title: '2000', id: 5 },
            { title: '4000', id: 6 }
          ]
        }
      ]
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
