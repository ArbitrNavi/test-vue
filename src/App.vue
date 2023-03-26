<template>
  <div class="background">
    <div class="container">
      <div v-for="timer in timers" v-bind:key="timer.id">
        <timer />
      </div>
      <div @click="addTimer" class="addTimerBlock">
        <p>+</p>
      </div>
    </div>
  </div>
</template>

<script>
import timer from "@/components/timer";

export default {
  name: 'App',
  components: {
    timer
  },
  data: function (){
    return {
      timers: [
        {id: 1}
      ]
    }
  },
  methods: {
    addTimer: function (){
      this.timers.push({id: this.timers.length + 1})
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

* {
  font-family: 'Roboto', sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.container{
  max-width: 780px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  gap: 50px;
}


.background {
  background: #353638;
  min-height: 100vh;
  padding: 70px 50px;

}

.addTimerBlock{
  width: 225px;
  height: 120px;
  background: #696969;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  user-select: none;
}

.addTimerBlock p {
  color: #9E9E9E;
  font-size: 40px;
  line-height: 20px;
}

</style>
