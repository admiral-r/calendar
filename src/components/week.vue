<template>
  <div class="calendar-week user-select-none">
    <span class="calendar-week-content">{{item.title}}</span>
  </div>
</template>
<script scoped>
export default {
  name: 'week',
  props: {
    item: Object,
  },
}
</script>
  
<style scoped>
.calendar-week {
  flex: 0 0 11%;
  padding: 0 .50rem;
  margin: 1.5%;
}

.calendar-week-content {
  font-size: .9rem;
  font-weight: 500;
}

@media only screen and (max-width: 600px) {
  .calendar-week-content {
    font-size: .6rem;
    font-weight: 600;
  }
}
</style>