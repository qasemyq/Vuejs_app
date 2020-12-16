<template>
    <div>
        <h1>Events Listing</h1>
        <EventCart v-for="event in events" :key="event.id" :event="event"/>
    </div>
</template>

<script>
import EventCart from '@/components/EventCart.vue'
import EventService from '@/services/EventService.js'

export default {
  components: {
    EventCart
  },
  data(){
    return {
      events: []
    }
  },
   created(){
     EventService.getEvents()
      .then(response => {
        this.events = response.data
   })
   .catch(error => {
     console.log('There was an error:' +error.response);
   })
   }
}







  // methods: {
  //   async test(){
  //     const res =await
  //     axios.get('/todos')
  //       console.log(res)
  //   }
  // },
  // mounted(){
  //   this.test()
  // }
</script>