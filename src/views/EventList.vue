<template>
  <div class="home">
    <div class="flex-center">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
   
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from '@/services/EventsService.js';

export default {
  name: "EventList",
  components: {
    EventCard,
  },
  data(){
    return {
      events: null
    }
  },
  created(){
    EventService.getEvents()
      .then(response => {
        this.events = response.data;
        console.log('events:', response.data);
      })
      .catch(error => {
        console.log(error)
      })
  }
};
</script>

