<template>
  <div id="app">
    <h1>Virtual Scrolling Component</h1>
  <virtual-scroll v-bind:arr_prop="arr"></virtual-scroll>
  </div>
</template>

<script>
import VirtualScroll from './components/VirtualScroll.vue'

export default {
  name: 'App',
  components: {
    VirtualScroll
  },

  data() {
    return {
        arr: ["FOO1","FOO2","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO","FOO00","FOO001"]
        }
    },
}

</script>

<style>

</style>
