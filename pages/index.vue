<template lang="pug">
  section.container
    .box
      h1.title {{hour}}:{{min}}
      button.btn(v-on:click="APlus") start
      button.btn(v-on:click="Rest") reset
</template>

<script>
export default {
  data () {
    return {
      time: 0,
      isStart: 0
    }
  },
  computed: {
    min: function () {
      var min = this.time % 60
      if (min < 10) {
        min = '0' + min
      }
      return min
    },
    hour: function () {
      var hour = Math.floor(this.time / 60)
      if (hour < 10) {
        hour = '0' + hour
      }
      return hour
    }
  },
  methods: {
    APlus: function () {
      this.isStart++
      this.time++
      setTimeout(() => { if (this.isStart) { this.APlus() } }, 1000)
    },
    Rest: function () {
      this.time = 0
      this.isStart = 0
    }
  }
}
</script>

<style lang="sass">
.container 
  min-height: 100vh
  display: flex
  justify-content: center
  align-items: center
  text-align: center
  background-color: #252525


.title 
  font-family: 'Concert One', cursive
  display: block
  font-weight: 300
  font-size: 100px
  color: #35495e
  letter-spacing: 1px
  color: white


.subtitle 
  font-weight: 300
  font-size: 42px
  color: #526488
  word-spacing: 5px
  padding-bottom: 15px


.links 
  padding-top: 15px

.btn
  font-family: 'Concert One', cursive
  color: white
  background: none
  font-size: 30px
  border: none
  padding: 5px 15px
  outline: none

</style>
