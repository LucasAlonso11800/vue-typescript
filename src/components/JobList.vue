<template>
  <div class="job-list">
    <p>Ordered by {{ order }}</p>
    <ul>
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }}USD</p>
        </div>
        <div class="description">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat
          eligendi explicabo modi saepe ipsum sit impedit pariatur illo, facere
          corrupti! Accusamus enim possimus, dolorem quasi obcaecati reiciendis
          dignissimos aut alias?
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import { JobType, OrderType } from "@/types";

export default defineComponent({
  name: "JobList",
  props: {
    jobs: {
      required: true,
      type: Object as PropType<JobType[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderType>,
    },
  },
  setup(props) {
    const orderedJobs = computed(() => {
      return [...props.jobs].sort((a, b) => (a[props.order] > b[props.order] ? 1 : -1));
    });
    return { orderedJobs };
  },
});
</script>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
</style>