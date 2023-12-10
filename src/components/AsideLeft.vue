<script setup>
import { userWatchList } from '../data/watchList'
import { defineProps, onMounted, ref } from 'vue'

const props = defineProps({
  test: {
    type: Object,
    default: null
  }
})

const liste = userWatchList

// Définir display comme une ref pour avoir les propriétées dynamiques.
const display = ref([])

const fillDisplay = () => {
  for (let i = 0; i < liste.length; i++) {
    if (liste[i].timeCursor !== '00:00:00') {
      // Aller chercher la proprité "value pour remplir"
      display.value.push(liste[i].title)
    }
  }
  console.log(display.value)
  return display.value
}

onMounted(() => {
  fillDisplay()
})
</script>

<template>
  <div class="col left">
    <h2>Série en cours</h2>
    <ul>
      
      <li v-for="(item, index) in display" :key="index">{{ item }}</li>
    </ul>
    <span v-if="props.test">▶ Lecture en cours: {{ props.test.series }}</span>
    <span v-else>▶ Aucune lecture en cours</span>
  </div>
  <div class="col right"></div>
</template>
