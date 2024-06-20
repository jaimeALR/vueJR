<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="logo site" />
        <h1>Hyrule Jobs</h1>
        <img src="./assets/work.svg" alt="logo site" />
      </div>
      <div v-if="showModal">
        <JobDescription :Jobs="jobs" />
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm";
import JobDescription from "./components/JobDescription.vue";

export default defineComponent({
  name: "App",
  components: { JobList, JobDescription },
  data() {
    return {
      showModal: false,
    };
  },
  setup() {
    const jobs = ref<Job[]>([
      { title: "farm worker", location: "Brazil", salary: 3000, id: "1" },
      {
        title: "Software Developer",
        location: "Germany",
        salary: 80000,
        id: "2",
      },
      { title: "Teacher", location: "Canada", salary: 50000, id: "3" },
      { title: "Nurse", location: "Australia", salary: 60000, id: "4" },
      {
        title: "Graphic Designer",
        location: "United States",
        salary: 55000,
        id: "5",
      },
      { title: "Civil Engineer", location: "India", salary: 40000, id: "6" },
      {
        title: "Data Analyst",
        location: "United Kingdom",
        salary: 70000,
        id: "7",
      },
      { title: "Chef", location: "France", salary: 45000, id: "8" },
      { title: "Marketing Manager", location: "Japan", salary: 75000, id: "9" },
      { title: "Electrician", location: "Mexico", salary: 30000, id: "10" },
      { title: "Lawyer", location: "South Africa", salary: 90000, id: "11" },
    ]);
    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

/* Button styles */
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

/* Header title styles */
header .title {
  display: flex;
  justify-content: center;
}

header img {
  width: 60px;
  margin: 20px;
}

header h1 {
  font-size: 3em;
}
</style>
