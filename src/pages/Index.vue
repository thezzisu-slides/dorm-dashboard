<template>
  <q-page class="column justify-center items-center">
    <div id="main" class="embed row justify-center items-center">
      <div class="board">
        <greeting />
      </div>
    </div>
    <div class="q-pt-md">
      <q-btn label="全屏" color="primary" @click="makeFullscreen" />
    </div>
  </q-page>
</template>

<script lang="ts" setup>
import Greeting from 'src/components/Greeting.vue'
import { onMounted } from 'vue'

onMounted(() => {
  const main = document.getElementById('main')!
  main.addEventListener('fullscreenchange', (ev) => {
    if (document.fullscreenElement) {
      main.classList.remove('embed')
    } else {
      main.classList.add('embed')
    }
  })
})

function makeFullscreen() {
  const main = document.getElementById('main')!
  main.requestFullscreen({ navigationUI: 'hide' })
}
</script>

<style>
.board {
  width: 1024px !important;
  height: 600px !important;
}

#main.embed {
  border: 1px solid #ccc;
  box-sizing: content-box;
}
</style>
