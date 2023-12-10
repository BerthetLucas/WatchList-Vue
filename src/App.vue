<script setup>
import AsideLeft from './components/AsideLeft.vue'
import ContentList from './components/ContentList.vue'
import { defineProps, ref } from 'vue'

// const { item } = defineProps(['item'])

const props =  defineProps({
    item :{
      type: Object, 
    }
})

const itemToAside = ref(null)

const onContinue = (item) => {
  itemToAside.value = item
}
</script>

<template>
  <div class="row">
    <AsideLeft :test="itemToAside" />
    <ContentList @continue="onContinue" />
  </div>
</template>
