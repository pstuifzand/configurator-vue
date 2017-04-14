<template>
  <div class="box choice is-half">
    <config-choice-title :title="choice.title" :selected="choice.selected" />

      <div class="options box" v-show="choice.open">
        <config-choice-type-select :choice="choice" @choosen="choosen" v-if="choice.type == 'select'"/>
          <config-choice-type-radio :choice="choice" @choosen="choosen"  v-if="choice.type == 'radio'" />
      </div>
  </div>
</template>

<style>
</style>

<script>

import ChoiceTitle from './ChoiceTitle'
import ChoiceTypeRadio from './ChoiceTypeRadio'
import ChoiceTypeSelect from './ChoiceTypeSelect'

export default {

  name: 'config-choice',

  components: {
    'config-choice-title': ChoiceTitle,
    'config-choice-type-radio': ChoiceTypeRadio,
    'config-choice-type-select': ChoiceTypeSelect
  },

  props: ['choice'],

  methods: {
    choosen (id) {
      this.$emit('choosen', id)
    }
  }
}
</script>
