<template>
  <div class=" calendar text-center p-4 bg-white position-absolute top-50 start-50 translate-middle">
    <div class="w-100">
      <month></month>
    </div>
  </div>
</template>
<script scoped>
import month from "./components/month.vue";
export default {
  name: "Calendar",
  components: { month },
};
</script>

<style scoped>
.calendar {
  width: 450px;
  height: 510px;
}

@media only screen and (max-width: 600px) {
  .calendar {
    width: 350px;
    height: 490px;
  }
}
</style>