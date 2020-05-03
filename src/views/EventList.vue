<template>
    <div>
        <h1>Event List</h1>
        <template v-if="!isLoading" >
            <EventCard v-for="event in events" :key="event.id" :event="event" />
        </template>
        <p v-else>Loading Events...</p>
    </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue';
import EventService from '@/services/EventService.js';

export default {
    components: {
        EventCard
    },
    data() {
        return {
            isLoading: true,
            events: []
        }
    },
    created(){
        EventService.getEvents()
        .then(response => {
            this.events = response.data
            this.isLoading = false
        })
        .catch(error => {
            console.log('There was an error ' + error.response)
        })
    }
}
</script>
