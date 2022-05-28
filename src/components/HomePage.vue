<template>
  <header-item class="code" />
  <job-listings class="code" />
</template>

<script>
import HeaderItem from "./HeaderItem.vue";
import JobListings from "./JobListings.vue";

export default {
  components: { JobListings, HeaderItem },
};
</script>

<style scoped>
</style>