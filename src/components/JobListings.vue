<template>
  <div>
    <div class="container">
      <div v-for="job in jobLists" :key="job.id">
        <job-item :job="job" />
      </div>
    </div>
  </div>
</template>

<script>
import jobLists from "../../public/data.json";
import JobItem from "./JobItem.vue";

export default {
  components: { JobItem },

  data() {
    return {
      jobLists,
    };
  },
};
</script>

<style scoped>
.container {
  margin: 0 4em;
}

.header img {
  width: 100%;
  height: auto;
}

@media only screen and (max-width: 375px),
  (min-width: 375px) and (max-width: 768px) {
  .container {
    margin: 0 1.5em;
  }
}

@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .container {
    margin: 0 3em;
  }
}

@media only screen and (min-width: 1024px) and (min-width: 1400px) {
  .container {
    margin: 0 6em;
  }
}
</style>