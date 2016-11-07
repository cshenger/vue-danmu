<template lang="html">
  <span class="move" :style="stylePosition">{{ lists }}</span>
</template>

<script>
export default {
  name: 'spanList',
  props: ['lists'],
  data () {
    let colorArr = ['#DC143C', '#EE7AE9', '#9BCD9B', '#1874CD', '#FFA500', '#FFFFFF', '#ADFF2F', '#EEEE00', '#68228B', '#BBFFFF']
    let topR = Math.floor(Math.random() * 90)
    let rightR = -Math.floor(Math.random() * 40 + 10)
    let colorR = colorArr[Math.floor(Math.random() * 10)]

    return {
      stylePosition: {
        top: topR + '%',
        right: rightR + '%',
        color: colorR
      }
    }
  },
  computed: {},
  methods: {}
}
</script>
