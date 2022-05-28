<template>
  <div>
    <div class="container">
      <JobFilterCard :tags="tags" @clicked="onClickTag" />
      <JobItem
        v-for="job in jobs"
        :key="job.id"
        :job="job"
        @clicked="onClickJob"
      />
    </div>
  </div>
</template>

<script>
import JobFilterCard from "./JobFilterCard.vue";
import JobItem from "./JobItem.vue";

export default {
  components: {
    JobFilterCard,
    JobItem,
  },

  data() {
    return {
      tags: [],
      jobs: [],
      jsonData: [
        {
          id: 1,
          company: "Photosnap",
          logo: "./images/photosnap.svg",
          new: true,
          featured: true,
          position: "Senior Frontend Developer",
          role: "Frontend",
          level: "Senior",
          postedAt: "1d ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["HTML", "CSS", "JavaScript"],
          tools: [],
        },
        {
          id: 2,
          company: "Manage",
          logo: "./images/manage.svg",
          new: true,
          featured: true,
          position: "Fullstack Developer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "1d ago",
          contract: "Part Time",
          location: "Remote",
          languages: ["Python"],
          tools: ["React"],
        },
        {
          id: 3,
          company: "Account",
          logo: "./images/account.svg",
          new: true,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2d ago",
          contract: "Part Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
        },
        {
          id: 4,
          company: "MyHome",
          logo: "./images/myhome.svg",
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "5d ago",
          contract: "Contract",
          location: "USA Only",
          languages: ["CSS", "JavaScript"],
          tools: [],
        },
        {
          id: 5,
          company: "Loop Studios",
          logo: "./images/loop-studios.svg",
          new: false,
          featured: false,
          position: "Software Engineer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "1w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["Ruby", "Sass"],
        },
        {
          id: 6,
          company: "FaceIt",
          logo: "./images/faceit.svg",
          new: false,
          featured: false,
          position: "Junior Backend Developer",
          role: "Backend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "UK Only",
          languages: ["Ruby"],
          tools: ["RoR"],
        },
        {
          id: 7,
          company: "Shortly",
          logo: "./images/shortly.svg",
          new: false,
          featured: false,
          position: "Junior Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["HTML", "JavaScript"],
          tools: ["Sass"],
        },
        {
          id: 8,
          company: "Insure",
          logo: "./images/insure.svg",
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["Vue", "Sass"],
        },
        {
          id: 9,
          company: "Eyecam Co.",
          logo: "./images/eyecam-co.svg",
          new: false,
          featured: false,
          position: "Full Stack Engineer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "3w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript", "Python"],
          tools: ["Django"],
        },
        {
          id: 10,
          company: "The Air Filter Company",
          logo: "./images/the-air-filter-company.svg",
          new: false,
          featured: false,
          position: "Front-end Dev",
          role: "Frontend",
          level: "Junior",
          postedAt: "1mo ago",
          contract: "Part Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
        },
      ],
    };
  },

  props: {
    msg: String,
  },

  created() {
    this.jobs = this.updateJobs(this.jsonData, this.tags);
  },

  methods: {
    updateJobs: function (jobs, tags) {
      console.log(tags);

      var newjobs = [];

      if (tags.length === 0) {
        return jobs;
      }

      jobs.forEach((job) => {
        var job_tags = [job.role, job.level, ...job.languages, ...job.tools];
        var all_in = true;

        for (let i = 0; i < tags.length; i++) {
          if (!job_tags.includes(tags[i])) {
            all_in = false;
          }
        }

        if (all_in) {
          newjobs.push(job);
        }
      });

      return newjobs;
    },

    onClickJob: function (value) {
      if (!this.tags.includes(value)) {
        this.tags.push(value);
        this.jobs = this.updateJobs(this.jsonData, this.tags);
      }
    },

    onClickTag: function (value) {
      if (value == "clearTags") {
        this.tags = [];
      } else {
        this.tags = this.tags.filter(function (item) {
          return item !== value;
        });
      }
      this.jobs = this.updateJobs(this.jsonData, this.tags);
    },
  },
};
</script>

<style scoped>
.container {
  margin: 0 4em;
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