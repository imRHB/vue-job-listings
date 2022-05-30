<template>
  <div class="job-filter-card">
    <div class="filtered-items">
      <div class="item-card" v-for="(tag, idx) in tags" :key="idx">
        <div class="item">{{ tag }}</div>
        <div class="close" @click="filter(tag)">X</div>
      </div>
    </div>

    <span class="filter-alt" v-show="tags.length === 0">
      Click on the skill item to filter jobs
    </span>

    <div class="clear" @click="clear()" v-show="tags.length !== 0">Clear</div>
  </div>
</template>

<script setup>
import { defineEmits, defineProps } from "vue";

const emit = defineEmits(["clicked"]);

defineProps({
  tags: Array,
});

const filter = (tag) => {
  emit("clicked", tag);
};

const clear = () => {
  emit("clicked", "clearTags");
};
</script>

<style scoped>
.job-filter-card {
  margin: 40px 0;
  margin-top: -40px;
  padding: 32px 24px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: center;
  background: #fff;
  box-shadow: 0 0 24px 1px rgba(0, 0, 0, 0.08);
  border-radius: 4px;
  transition: 0.4s;
}

.filter-alt {
  color: hsl(180, 29%, 50%);
}

.filtered-items {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.clear {
  color: hsl(180, 29%, 50%);
}

.clear:hover {
  cursor: pointer;
  text-decoration: underline;
}

.item-card {
  display: flex;
}

.item {
  padding: 8px;
  color: hsl(180, 29%, 50%);
  background-color: hsl(180, 31%, 95%);
  border-radius: 3px 0 0 3px;
}

.close {
  padding: 8px 12px;
  color: hsl(180, 31%, 95%);
  background-color: hsl(180, 29%, 50%);
  border-radius: 0 3px 3px 0;
  cursor: pointer;
}

.close:hover {
  background-color: hsl(180, 14%, 20%);
}

@media only screen and (max-width: 375px),
  (min-width: 375px) and (max-width: 768px) {
  .container {
    margin: 0 1.5em;
  }

  .job-filter-card {
    display: flex;
    gap: 16px;
    margin: 70px 0px;
    margin-top: -40px;
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