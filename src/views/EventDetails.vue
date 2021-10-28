<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'
export default {
  name: 'EventDetails',
  props: ['id'],
  data() {
    return {
      event: null
    }
  },
  async created() {
    try {
      const eventData = await EventService.getEvent(this.id)
      this.event = eventData.data
    } catch (error) {
      console.log(error)
    }
  }
}
</script>
