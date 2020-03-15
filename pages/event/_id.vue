
<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Event: ' + this.event.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'What you need to know about Event ' + this.event.title
        }
      ]
    }
  },
  async asyncData({ $axios, error, params }) {
    try {
      // here we use es6 desctrutoring - it could also just be const response
      const { data } = await $axios.get(
        'http://localhost:3000/events/' + params.id
      )
      return {
        // this merge with the componet data!! and events can just get used in the template
        event: data
      }
    } catch (e) {
      error({
        // this renders the error page with the message if we have a error
        statusCode: 503,
        message: 'Unable to fetch event #' + params.id + '. Please try again.'
      })
    }
  }
}
</script>

<style scoped>
</style>
