<template>
  <div class="container-clock">
    <h1>Reloj</h1>
    <div class="clockScreen">
      <div class="screen" :style="styleSet">
        <div class="hours">
          <p>{{ hours }}</p>
        </div>
        <p>{{ meridiem }}</p>
        <!-- <p>{{ day }}</p> -->
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      hours: ":)",
      minutes: 0,
      seconds: 0,
      meridiem: "",
      day: "",
    };
  },
  props: {
    styleSet: {
      type: Object,
    }
  },

  methods: {
    getDate() {
      const date = new Date();
      let hours = date.getHours();
      let minutes = date.getMinutes();
      let seconds = date.getSeconds();
      const day = date.toDateString();
      hours = hours <= 9 ? `${hours}`.padStart(2, 0) : hours;
      minutes = minutes <= 9 ? `${minutes}`.padStart(2, 0) : minutes;
      seconds = seconds <= 9 ? `${seconds}`.padStart(2, 0) : seconds;
      this.hours = `${hours} : ${minutes} : ${seconds} `;
      this.minutes = minutes;
      this.seconds = seconds;
      this.meridiem = hours >= 12 ? "PM" : "AM";
      this.day = day;
    },
  },

  mounted() {
    setInterval(() => this.getDate(), 1000);
  },
};
</script>

<style scoped>
.container-clock {
  background: aquamarine;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 10px;
}

.clockScreen {
  width: 450px;
  height: 420px;
  background-color: #8e8e8e;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.screen {
  width: 420px;
  height: 390px;
  font-size: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: white;
  gap: 25px;
  border-radius: 50%;
}
</style>
