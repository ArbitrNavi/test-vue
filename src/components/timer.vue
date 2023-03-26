<template>
  <div class="timer">
    <div class="timer-top" v-bind:class="{stop: startValue}">
      <h1>
        <span v-if="hour > 0">{{ hour }}:</span><span v-if="minute > 0 || hour !== 0">{{ minute }}:</span>{{ second }}
      </h1>
    </div>
    <div  class="timer-bottom" v-bind:class="{stop: startValue}">
      <button v-if="this.startValue === true" @click="start" class="btn-start"></button>
      <p v-if="this.startValue === false" @click="stop" class="btn-stop">=</p>
      <button @click="reset" class="btn-reset"></button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TheTimer',
  components: {},
  data: function () {
    return {
      hour: 0,
      minute: 0,
      second: 0,
      startValue: true,
    }
  },
  methods: {
    timer: function () {
      if (this.startValue !== true){
        if (this.second < 60) {
          this.second++
          console.log(this.second)
          setTimeout(() => {
            this.timer();
          }, 1000)
          if (this.second === 60) {
            this.minute++
            console.log(this.minute)
            this.second = 0;
          }
          if (this.minute === 60) {
            this.hour++
            this.minute = '0';
          }
        }
      }
    },

    start: function () {
      this.startValue = false;
      if (this.startValue === false) {
        this.timer();
      }
    },
    stop: function () {
      this.startValue = !this.startValue
    },
    reset: function () {
      this.second = 0;
      this.minute = 0;
      this.hour = 0;
      this.startValue = true;
    }
  }
}
</script>

<style>

.stop{
  filter: brightness(0.7);
}


.btn-start {
  width: 17px;
  height: 20px;
  border: 0;
  background: transparent;
  cursor: pointer;
}

.btn-start {
  width: 0;
  height: 0;
  border-width: 8.5px 0 8.5px 14.7px;
  border-color: transparent transparent transparent #fff;
  border-style: solid;
}

.btn-stop {
  border: 0;
  width: 10px;
  line-height: 10px;
  font-size: 40px;
  writing-mode: vertical-rl;
  cursor: pointer;
}

.btn-reset {
  width: 20px;
  height: 20px;
  background: #fff;
  border: 0;
}

.timer-top {
  height: calc(100% / 2);
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #fff;
}

.timer-bottom {
  height: calc(100% / 2);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 50px;
}

.timer {
  color: #fff;
  width: 225px;
  height: 120px;
  background: #696969;
}
</style>