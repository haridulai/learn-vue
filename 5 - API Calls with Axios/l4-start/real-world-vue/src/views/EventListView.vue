<script setup>
import EventCard from '@/components/EventCard.vue'
import axios from 'axios';
import { ref, onMounted } from 'vue'

const events = ref(null)

onMounted(() => {
  axios
  .get('https://my-json-server.typicode.com/haridulai/api/events')
  .then((response) => {
    console.log(response.data);
  })
  .catch((error) => {
    console.log(error);
  })
})
</script>

<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
