<template>
  <div class="schedule-course">
    <h1>Make a course schedule</h1>
    <get-course v-if="step == 1"></get-course>
  </div>
</template>

<script>
import GetCourse from './GetCourse';

export default {
  components: {
    GetCourse
  },
  data: () => ({
    step: 1,
    selectedCourse: null
  })
};
</script>
