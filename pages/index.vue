<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue'
export default {
  head() {
    return {
      title: 'Event Listing' // Title for the page
    }
  },
  // asyncData(context) {
  // return context.$axios.get('http://localhost:3000/events').then(response => {
  // or use es6 destructoring
  // asyncData({ $axios, error }) {
  //   return $axios
  //     .get('http://localhost:3000/events')
  //     .then(response => {
  //       return {
  //         // this merge with the componet data!! and events can just get used in the template
  //         events: response.data
  //       }
  //     })
  //     .catch(e => {
  //       error({
  //         // this renders the error page with the message if we have a error
  //         statusCode: 503,
  //         message: 'Unable to fetch events at this time. Please try again.'
  //       })
  //     })
  // },
  async asyncData({ $axios, error }) {
    try {
      // here we use es6 desctrutoring - it could also just be const response
      const { data } = await $axios.get('http://localhost:3000/events')
      return {
        // this merge with the componet data!! and events can just get used in the template
        events: data
      }
    } catch (e) {
      error({
        // this renders the error page with the message if we have a error
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.'
      })
    }
  },
  components: {
    EventCard
  }
}
</script>
