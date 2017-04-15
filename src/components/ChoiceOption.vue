<template>
  <div class="field">
    <p class="control is-expanded">
      <label class="radio" style="width:100%">
        <input type="radio" class="radio" :name="this.name" :value="option.id" @click="changeSelected">
        {{ option.title }}
      </label>
    </p>
  </div>
</template>

<script>
export default {
  name: 'config-choice-option',

  props: ['option', 'choiceId'],

  methods: {
    changeSelected () {
      this.$emit('selected', this.choiceId, this.option.id)
    }
  },

  computed: {
    name () {
      return 'choice-' + this.choiceId
    }
  }
}
</script>
