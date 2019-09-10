<template>
  <div>
    <!-- <v-btn @click="getCourseList()" color="primary">Click!</v-btn> -->
    <v-expansion-panels>
        <v-expansion-panel v-for="(item, idx) in courses" :key="idx">
            <v-expansion-panel-header>
                <h3>{{ item.title }}</h3>
            </v-expansion-panel-header>
            <v-expansion-panel-content>
                기간 : {{ item.duration }} 시간 <br/>
                최소 인원 : {{ item.minEnrollment }} <br/>
                최대 인원 : {{ item.maxEnrollment }} <br/>
                수업료 : {{ item.unitPrice }} <br/>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn text color="primary">Select</v-btn>
                </v-card-actions>
            </v-expansion-panel-content>
        </v-expansion-panel>
    </v-expansion-panels>
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
            .catch(e => { console.log(e)});
        }
    },
    created() {
        this.getCourseList();
    }
}
</script>

<style>

</style>