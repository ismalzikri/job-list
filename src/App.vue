<template>
  <div class="app">
    <span><b>simple.career.com</b></span>
    <header>
      <div class="order">
        <button @click="handleClick('title')">Find by title</button>
        <button @click="handleClick('salary')">Find by salary</button>
        <button @click="handleClick('location')">Find by location</button>
      </div>

    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/jobsList.vue";
import Job from "./types/job";
import OrderTerm from "./types/OrderTerm"

export default defineComponent({
  name: "App",
  components: {
    JobList,
  },
  setup() {
    const jobs = ref<Job[]>([
      { title: "FrontEnd Engineer", location: "medan", salary: 50000, id: "1" },
      { title: "BackEnd Engineer", location: "jakarta", salary: 50000, id: "2" },
      { title: "Devops Engineer", location: "Malang", salary: 70000, id: "3" },
      { title: "UI/UX designer", location: "Aceh", salary: 60000, id: "4" },
    ]);


    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order };
  },
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    padding-top: 100px;
  }
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
  span {
    color: #1195c9;
    font-size: 1.5em;
    position: fixed;
    margin: 0;
  }
</style>
