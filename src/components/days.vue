<template>
  <div class="user-select-none" :class="date !== null ? 'calendar-days' : 'calendar-days-null'">
    <span ref="day" class="calendar-days-content">{{date !== null ? date.getDate() : ""}}</span>
  </div>
</template>
<script scoped>
export default {
  name: "days",
  props: {
    day: {
      type: Number,
    },
    date: {
      type: Object,
    },
  },
  mounted() {
    if (this.$refs.day.innerHTML == this.day) {
      this.$refs.day.classList.add("text-primary" , 'h5');
    }
  },
  updated() {
    this.$refs.day.classList.remove("text-primary" , 'h5');
  },
};
</script>

<style scoped>
.calendar-days {
  flex: 0 0 11%;
  padding: 1.8%;
  border-radius: 6px;
  margin: 1.5%;
}

.calendar-days-null {
  flex: 0 0 11%;
  padding: 1.8%;
  border-radius: 6px;
  margin: 1.5%;
}
</style>