<template>
  <div class="columns">
    <div class="column">
      <div class="field">
        <p class="control is-expanded">
          <span class="select is-fullwidth">
            <select :name="choice.name" @click="choosen" v-model="current">
              <option :value="option.id" v-for="option in choice.options">
                {{ option.title }}
              </option>
            </select>
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'config-choice-type-select',

  props: ['choice'],

  data () {
    return {
      'current': null
    }
  },

  methods: {
    choosen () {
      this.$emit('choosen', this.choice.id, this.current)
    }
  }
}
</script>
