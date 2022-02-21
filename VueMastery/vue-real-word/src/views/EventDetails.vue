<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import { getEvent } from '@/services/eventService.js'

export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  async created() {
    const response = await getEvent(this.id)
    console.log(response.data)
    this.event = response.data
  },
}
</script>
