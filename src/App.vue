<template>
  <div id="app">
    <div class="danmu">
      <board></board>
      <box-input></box-input>
    </div>
  </div>
</template>

<script>
import Board from './components/board.vue'
import BoxInput from './components/boxInput.vue'

export default {
  name: 'app',
  components: {
    Board,
    BoxInput
  }
}
</script>

<style src="./css/App.css"></style>
