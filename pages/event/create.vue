<template>
  <div>
    <h1>Create an Event</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Crate an Event', // Title for the page - plus the extra form the template in layouts/default.vue
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'Whre you can create a new event taking place in your neighborhood' // Description for the page
        }
      ]
    }
  }
}
</script>
