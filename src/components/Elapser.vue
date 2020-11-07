<template>
  <div class="container">
    <span class="years">
      {{ elapserYears }} years
    </span>
    <span class="months">
      {{ elapserMonths }} months
    </span>
    <span class="days">
      {{ elapserDays }} days
    </span>
    <span class="hours">
      {{ elapserHours }} hours
    </span>
    <span class="minutes">
      {{ elapserMinutes }} minutes
    </span>
    <span class="seconds">
      {{ elapserSeconds }} seconds
    </span>
  </div>
</template>

<script>
export default {
  name: "Elapser",
  data() {
    return {
      elapserYears: 0,
      elapserMonths: 0,
      elapserDays: 0,
      elapserHours: 0,
      elapserMinutes: 0,
      elapserSeconds: 0,
    }
  },
  mounted() {
    this.getTime();
    setInterval(this.getTime, 1000);
  },
  methods: {
    getTime() {
      const startDate = new Date("Fri Jan 17 2020 17:45:00 GMT+0100 (Central European Standard Time)");
      // const currentDate = new Date("Fri Jan 17 2022 17:45:00 GMT+0100 (Central European Standard Time)");
      const currentDate = new Date();

      let deltaTime = currentDate.getTime() - startDate.getTime();
      let deltaDate = new Date(deltaTime);
      console.log(deltaDate);


      //FUCKS SAKE MANNN
      this.elapserYears = (deltaDate.getFullYear() - 1970).toString();
      this.elapserMonths = (deltaDate.getMonth()).toString();
      this.elapserDays = (deltaDate.getDate() - 1).toString();
      this.elapserHours = (deltaDate.getHours() - 1).toString();
      this.elapserMinutes = (deltaDate.getMinutes()).toString();
      this.elapserSeconds = (deltaDate.getSeconds()).toString();

    },
  }
}
</script>

<style scoped>
.container {
  font-size: 36px;
  font-family: monospace;
  color: var(--white-text);
  padding: 32px 0;
}
</style>
