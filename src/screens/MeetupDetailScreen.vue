<template>
  <nb-container>
    <nb-h1 :style="[styles.headerOne, styles.container]">{{meetup.title}}</nb-h1>
      <nb-thumbnail :source="{uri: meetupCreator.avatar}"/>
    <nb-text :style="{paddingLeft: 20}">
    By {{meetupCreator.name}}
    </nb-text>
    <nb-content>
      <nb-card>
        <nb-card-item header bordered>
          <nb-text>Details</nb-text>
        </nb-card-item>
        <nb-card-item bordered>
          <nb-body>
            <nb-text :style="styles.label">
              Date
            </nb-text>
            <nb-text :style="styles.padin">
              {{meetup.startDate}}
            </nb-text>
            <nb-text :style="styles.label">
              From
            </nb-text>
            <nb-text :style="styles.padin">
              {{meetup.timeFrom}}
            </nb-text>
            <nb-text :style="styles.label">
              To
            </nb-text>
            <nb-text :style="styles.padin">
              {{meetup.timeTo}}
            </nb-text>
            <nb-text :style="styles.label">
              Category
            </nb-text>
            <nb-text :style="styles.padin">
              {{category.name}}
            </nb-text>
            <nb-text :style="styles.label">
              Info
            </nb-text>
            <nb-text :style="styles.padin">
              {{meetup.shortInfo}}
            </nb-text>
          </nb-body>
        </nb-card-item>
        <nb-card-item header bordered>
          <nb-text :style="styles.padin">Description</nb-text>
        </nb-card-item>
        <nb-card-item bordered>
          <nb-body>
            <nb-text :style="styles.padin">
              {{meetup.description}}
            </nb-text>
          </nb-body>
        </nb-card-item>
      </nb-card>
    </nb-content>
  </nb-container>

</template>
<script>
import styles from '@/styles'
export default {
props:{
  navigation:{
    type: Object
  }
},
  data(){
  return{
    meetupId: '',
    styles
  }
  },
  computed:{
  meetup(){
    return this.$store.state.meetups.item
  },
    meetupCreator(){
      return this.meetup.meetupCreator || {}
    },
    category(){
      return this.meetup.category || {}
    }
  },
  created(){
  const meetupId = this.navigation.getParam('meetupId','undefined')
    this.$store.dispatch('meetups/fetchMeetupById', meetupId)
  }
}
</script>
<style></style>