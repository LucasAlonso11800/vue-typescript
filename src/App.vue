<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import JobList from "./components/JobList.vue";
import { JobType, OrderType } from "./types";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<JobType[]>([
      {
        title: "Farm Worker",
        salary: 30000,
        location: "Lon Lon Ranch",
        id: "1",
      },
      {
        title: "Quarryman",
        salary: 40000,
        location: "Death Mountain",
        id: "2",
      },
      { title: "Flute Player", salary: 35000, location: "Lost Woods", id: "3" },
      { title: "Fisherman", salary: 21000, location: "Lake Hylia", id: "4" },
      {
        title: "Prison Guard",
        salary: 32000,
        location: "Gerudo Valley",
        id: "5",
      },
    ]);
    const order = ref<OrderType>("title");
    const handleClick = (newOrder: OrderType) => (order.value = newOrder);
    return { jobs, order, handleClick };
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
</style>
