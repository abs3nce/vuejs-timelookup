<template>
  <div class="container">
    <div class="timer-input-field" v-if="isSubmitted < 0">
      <input type="text" class="time-input" v-model="timerHours"> Hours
      <input type="text" class="time-input" v-model="timerMinutes"> Minutes
      <input type="text" class="time-input" v-model="timerSeconds"> Seconds
    </div>
    <div class="timer-display" v-if="isSubmitted > 0">
      <span>{{ timerHours }}:</span><span>{{ timerMinutes }}:</span><span>{{ timerSeconds }}</span>
    </div>
    <br><br><input type="submit" class="timer-submit" @click="submitTime">
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
      isSubmitted: -1,
      seconds: 0,
    }
  },
  mounted() {
  },
  // methods: {
  //   submitTime() {
  //     this.isSubmitted *= -1;
  //     setInterval(this.countDown, 1000);
  //   },
  //   countDown() {
  //     let countDownTime = new Date("Nov 7, 2020, " + this.timerHours + ":" + this.timerMinutes + ":" + this.timerSeconds).getTime();
  //     let currentTime = new Date().getTime();
  //
  //     let timeDifference = currentTime - countDownTime;
  //
  //     this.timerHours = Math.abs(Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)));
  //     this.timerMinutes = Math.abs(Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60)));
  //     this.timerSeconds = Math.abs(Math.floor((timeDifference % (1000 * 60)) / 1000));
  //   }
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
