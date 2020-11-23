<template>
  <div class="container">
    <span class="hours">
      {{ clockHours }}
    </span>
    <span class="minutes">
      : {{ clockMinutes }}
    </span>
    <span class="seconds">
      : {{ clockSeconds }}
    </span>
  </div>
</template>

<script>
export default {
  name: "Clock",
  data() {
    return {
      clockHours: 0,
      clockMinutes: 0,
      clockSeconds: 0,
    }
  },
  mounted() {
    this.getTime();
    setInterval(this.getTime, 1000);
  },
  methods: {
    getTime() {
      let time = new Date();
      this.clockHours = time.getHours();
      this.clockMinutes = time.getMinutes();
      this.clockSeconds = time.getSeconds();
    }
  }
}
</script>

<style scoped lang="scss">
.container {
  font-size: 36px;
  font-family: monospace;
  color: var(--white-text);
  padding: 32px 0;
}
</style>
