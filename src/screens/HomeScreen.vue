

<template>
  <scroll-view>
    <nb-text class="header-1">Featured Meetups</nb-text>
    <MeetupCard v-for="meetup in meetups" :meetup="meetup" :key="meetup._id" :navigateToDetail="goToMeetupDetail"/>
  </scroll-view>
</template>

<script>
import  MeetupCard from '@/components/MeetupCard'
export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data () {
    return {
      title: 'Home Screen!'
    }
  },
  components:{
    MeetupCard
  },
  computed: {
    todos () {
      return this.$store.state.todos
    },
    meetups(){
      return this.$store.state.meetups.items
    }
  },
  created(){
    this.$store.dispatch('fetchTodos')
    this.$store.dispatch('meetups/fetchMeetups')
  },
  methods: {
    goToScreen1 () {
      this.navigation.navigate('ScreenOne')
    },
    goToMeetupDetail(meetupId){
      this.navigation.navigate('Meetup', {meetupId})
    }
  }
}
</script>

<style>
.header-1 {
  font-size: 23px;
  padding: 20px;
  font-weight: bold;
}
</style>