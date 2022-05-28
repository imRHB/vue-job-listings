<template>
  <div :class="job.new && job.featured ? 'card card-special' : 'card'">
    <div class="logo">
      <img :src="job.logo" alt="logo" />
    </div>

    <div class="job-details-sec">
      <div class="job-details">
        <div class="posting-details">
          <span class="company">{{ job.company }}</span>
          <small
            ><span :class="job.new ? 'new-job' : ' '">{{
              job.new ? "NEW" : ""
            }}</span></small
          >
          <small
            ><span :class="job.featured ? 'featured' : ' '">{{
              job.featured ? "FEATURED" : ""
            }}</span></small
          >
        </div>
        <div>
          <span class="position">{{ job.position }}</span>
        </div>
        <div class="type">
          {{ job.postedAt }}
          <span
            style="
               {
                fontsize: 4px;
                margin: 0px 6px;
              }
            "
          >
            -
          </span>
          {{ job.contract }}
          <span
            style="
               {
                fontsize: 4px;
                margin: 0px 6px;
              }
            "
          >
            -
          </span>
          {{ job.location }}
        </div>
      </div>

      <div class="hr-line">
        <!-- horizontal line -->
      </div>

      <div class="skills">
        <p class="skill" @click="filter(job.role)">{{ job.role }}</p>
        <p class="skill" @click="filter(job.level)">{{ job.level }}</p>
        <p
          class="skill"
          v-for="(language, idx) in job.languages"
          :key="idx"
          @click="filter(language)"
        >
          {{ language }}
        </p>
        <p
          class="skill"
          v-for="(tool, idx) in job.tools"
          :key="idx"
          @click="filter(tool)"
        >
          {{ tool }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  components: {},

  props: {
    job: Object,
  },

  methods: {
    filter: function (tag) {
      this.$emit("clicked", tag);
    },
  },
};
</script>

<style scoped>
.card {
  border-left: 4px solid transparent;
  display: flex;
  align-items: center;
  margin: 40px 0;
  padding: 24px;
  background-color: #fff;
  box-shadow: 0 4px 18px 0px rgba(0, 0, 0, 0.08);
  border-radius: 4px;
  transition: 0.4s;
}

.card-special {
  border-left: 4px solid hsl(180, 8%, 52%);
}

.card:hover {
  box-shadow: 0 4px 20px 2px rgba(0, 0, 0, 0.12);
}

.logo img {
  width: 72px;
  height: auto;
}

.job-details-sec {
  display: flex;
  flex: 1;
  gap: 16px;
  justify-content: space-between;
  align-items: center;
}

.job-details {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-left: 20px;
}

.posting-details {
  display: flex;
  align-items: center;
  gap: 8px;
  color: hsl(180, 29%, 50%);
}

.new-job,
.featured {
  font-size: 11px;
  padding: 4px 8px;
  border-radius: 16px;
  color: hsl(180, 31%, 95%);
}

.new-job {
  background-color: hsl(180, 29%, 50%);
}

.featured {
  background-color: hsl(180, 14%, 20%);
}

.position {
  font-weight: 700;
  color: hsl(180, 14%, 20%);
}

.position:hover {
  color: hsl(180, 29%, 50%);
  cursor: pointer;
}

.type {
  color: hsl(180, 8%, 52%);
  display: flex;
  align-items: center;
}

.hr-line {
  width: 100%;
  border-top: 2px solid hsl(180, 29%, 50%);
  display: none;
}

.skills {
  display: flex;
  flex-wrap: wrap;
  place-items: flex-end;
}

.skill {
  margin: 4px;
  padding: 6px;
  border-radius: 4px;
  color: hsl(180, 29%, 50%);
  background-color: hsl(180, 31%, 95%);
}

.skill:hover {
  color: hsl(180, 31%, 95%);
  background-color: hsl(180, 29%, 50%);
  cursor: pointer;
}

@media only screen and (max-width: 375px),
  (min-width: 375px) and (max-width: 768px) {
  .card {
    display: flex;
    flex-direction: column;
    gap: 16px;
    align-items: flex-start;
    margin: 70px 0px;
  }

  .logo img {
    width: 64px;
    height: auto;
    margin-top: -56px;
    margin-bottom: 12px;
  }

  .job-details-sec {
    display: flex;
    flex-direction: column;
    margin-left: 0px;
    place-items: flex-start;
  }

  .job-details {
    margin-left: 0px;
  }

  .hr-line {
    display: block;
  }
}
</style>