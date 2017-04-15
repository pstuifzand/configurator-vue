<template>
  <div class="columns">
    <div class="column">
      <config-choice-option 
         v-for="option in left"
         :option="option" :key="option.id"
         :choice-id="choice.id"
         @selected="choosen"
         >
      </config-choice-option>
    </div>

    <div class="column">
      <config-choice-option 
         v-for="option in right"
         :option="option" :key="option.id"
         :choice-id="choice.id"
         @selected="choosen"
         >
      </config-choice-option>
    </div>

  </div>
</template>

<script>
import _ from 'lodash'
import ChoiceOption from './ChoiceOption'

export default {
  name: 'config-choice-type-radio',
  components: {
    'config-choice-option': ChoiceOption
  },
  props: ['choice'],

  methods: {
    choosen (choiceId, optionId) {
      this.$emit('choosen', choiceId, optionId)
    }
  },

  computed: {
    left () {
      return _.take(this.choice.options, _.floor(this.choice.options.length / 2))
    },
    right () {
      return _.drop(this.choice.options, _.floor(this.choice.options.length / 2))
    }
  }
}
</script>
