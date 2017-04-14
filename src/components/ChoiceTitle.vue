<template>
  <div class="level">
    <div class="level-left">
      <div class="level-item">
        <span :class="boxClass" v-if="selected">
          <i class="fa fa-check-square-o"></i>
        </span>

        <span :class="boxClass" v-if="!selected">
          <i class="fa fa-square-o"></i>
        </span>
      </div>

      <div class="level-item">
        <h2 class="title is-4">{{ title }}</h2>
      </div>
    </div>
  </div>
</template>
<style>
.icon.is-info {
  color: green;
}
</style>

<script>
  export default {
    name: 'config-choice-title',
    props: ['selected', 'title'],
    computed: {
      boxClass () {
        return (this.selected ? 'icon is-info is-medium' : 'icon is-medium')
      }
    }
  }
</script>
