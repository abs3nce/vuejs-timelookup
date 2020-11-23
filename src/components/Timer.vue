<template>
  <div class="container">
    <div class="timer-input-field" v-if="!countDownActive">
      <input type="text" class="time-input" v-model="timerHours"> Hours
      <input type="text" class="time-input" v-model="timerMinutes"> Minutes
      <input type="text" class="time-input" v-model="timerSeconds"> Seconds
      <br><br><input type="submit" class="timer-submit" @click="startCountDown">
    </div>
    <div class="timer-display" v-if="countDownActive">
      <span>{{ timerHours }}:</span><span>{{ timerMinutes }}:</span><span>{{ timerSeconds }}</span>
    </div>
    <div class="alert" v-if="isOver">
      TIMER END
    </div>
  </div>
</template>

<script>
export default {
  name: "Timer",
  data() {
    return {
      timerHours: 0,
      timerMinutes: 0,
      timerSeconds: 0,
      countDownActive: false,
      isOver: false,
      totalTime: 0,
      intervalID: 0,
    }
  },
  mounted() {
  },
  methods: {
    startCountDown() {
      this.countDownActive = !this.countDownActive;
      this.intervalID = setInterval(this.updateCountDown, 1000);
      this.isOver = false;
    },
    updateCountDown() {
      this.timerSeconds--;
      if (this.timerSeconds === -1) {
        this.timerSeconds = 59;
        this.timerMinutes--;
      }
      if (this.timerMinutes === -1) {
        this.timerMinutes = 59;
        this.timerHours--;
      }
      if (this.timerHours < 0) {
        setTimeout(() => {
          this.isOver = false;
        }, 3000);
        this.isOver = true;
        this.stopCountDown();
      }
    },
    stopCountDown() {
      this.countDownActive = !this.countDownActive;
      clearInterval(this.intervalID);
      this.timerSeconds = 0;
      this.timerMinutes = 0;
      this.timerHours = 0;
    },
  }
  // }
}
</script>

<style scoped lang="scss">
.container {
  font-size: 24px;
  font-family: monospace;
  color: var(--white-text);
  padding: 32px 0;

  .timer-input-field {
    .time-input {
      background: none;
      border: none;
      border-bottom: 1px solid var(--white-text);
      color: var(--white-text);
      font-size: 24px;
      text-align: center;
    }
  }

  .timer-submit {
    width: 90%;
    padding: 16px;
    font-size: 24px;
    background: none;
    border: none;
    color: var(--white-text);
  }
}
</style>
