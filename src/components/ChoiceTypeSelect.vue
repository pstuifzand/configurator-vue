<template>
  <div class="columns">
    <div class="column">
      <div class="field">
        <p class="control is-expanded">
          <span class="select is-fullwidth">
            <select :name="choice.name" @change="choosen(choice.id)">
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

  methods: {
    choosen (id) {
      this.$emit('choosen', id)
    }
  }
}
</script>
