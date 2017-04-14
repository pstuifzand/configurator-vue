<template>
  <div id="app">
    <div class="columns">
      <div class="column">
        <section class="section">
          <configurator>
          </configurator>
        </section>
      </div>
      <div class="column">
      </div>
    </div>
  </div>
</template>

<script>
import Configurator from './components/Configurator'

export default {
  name: 'app',
  components: {
    Configurator
  }
}
</script>

<style>
#app {
}
</style>
