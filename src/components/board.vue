<template lang="html">
  <div class="main" :style="{ backgroundImage: bgImgUrl }">
    <section class="main_dan">
      <span-list v-for="lists in listArr" :lists="lists"></span-list>
    </section>
  </div>
</template>

<script>
import SpanList from './spanList.vue'
import Bus from './Bus.js'
import bgImg from '../assets/img.jpg'

let DANMU_VUE = 'danmu-vue'

let listArrGlobal = JSON.parse(window.localStorage.getItem(DANMU_VUE) || '[]')

Bus.$on('addLists', function (arg) {
  listArrGlobal.push(arg)
  window.localStorage.setItem(DANMU_VUE, JSON.stringify(listArrGlobal))
  console.log(listArrGlobal)
})

export default {
  name: 'board',
  data () {
    return {
      listArr: listArrGlobal,
      bgImgUrl: 'url(' + bgImg + ')'
    }
  },
  components: {
    SpanList
  }
}

function addMoveStyle () {
  let span = document.querySelectorAll('.main_dan span')
  let len = span.length

  for (let i = 0; i < len; i++) {
    span[i].setAttribute('class', '')
  }

  let j = 0
  let timer = null
  if (j < len) {
    timer = setInterval(function () {
      span[j].setAttribute('class', 'move')
      j++
      if (j === len) clearInterval(timer)
    }, 800)
  }
}

window.onload = function () {
  addMoveStyle()
}
</script>
