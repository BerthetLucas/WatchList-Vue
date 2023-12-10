<script setup>
import { userWatchList } from '../data/watchList'
import { defineEmits } from 'vue'

// Variable réactive
const liste = userWatchList

const emits = defineEmits(['continue'])
</script>

<template>
  <div class="col right">
    <div v-for="(item, index) in liste" :key="index" class="courses-container">
      <div class="course">
        <div class="course-preview">
          <h6>Season {{ item.season }}</h6>
          <h2>{{ item.series }}</h2>
        </div>
        <div class="course-info">
          <h6>ep: S0{{ item.season }}E0{{ item.episode }}</h6>
          <h2>{{ item.title }}</h2>
          <button class="btn" v-if="item.timeCursor == '00:00:00'">Start</button>
          <button
            class="btn"
            v-if="item.timeCursor !== '00:00:00'"
            @click="$emit('continue', item)"
          >
            Continue
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
