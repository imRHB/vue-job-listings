<template>
  <header-item />
  <!-- <job-filter-card /> -->
  <job-listings />
</template>

<script>
import HeaderItem from "./HeaderItem.vue";
// import JobFilterCard from "./JobFilterCard.vue";
import JobListings from "./JobListings.vue";

export default {
  components: { JobListings, HeaderItem },
};
</script>

<style scoped>
</style>