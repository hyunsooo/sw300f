<template>
  <div>
    <v-btn @click="getCourseList()" color="primary">Click!</v-btn>
    <v-expansion-panel>
        <v-expansion-panel-content v-for="(item, idx) in courses" :key="idx">
            <h3>{{ item.title }}</h3>
        </v-expansion-panel-content>
    </v-expansion-panel>
  </div>
</template>

<script>
export default {
    data() {
        return {
            courses: [
                {
                    "title": "Java 완전 정복"
                },
                {
                    "title": "SW300 완전 정복"
                }
            ]
        }
    },
    methods: {
        getCourseList() {
            this.$axios
            .get("http://13.124.69.97:8080/courses")
            .then(res => {
                console.log(res.data._embedded.course);
                this.courses = res.data._embedded.course;
            })
            .catch(e => console.log(e));
        }
    }
}
</script>

<style>

</style>