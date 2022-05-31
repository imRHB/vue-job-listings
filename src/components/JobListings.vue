<template>
  <div>
    <div class="container">
      <JobFilterCard :tags="selectedTags" @clicked="onDeselectTag" />
      <JobItem
        v-for="job in filteredJobs"
        :key="job.id"
        :job="job"
        @clicked="onSelectTag"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import JobFilterCard from "./JobFilterCard.vue";
import JobItem from "./JobItem.vue";

const selectedTags = ref([]);
const jobs = ref([
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
]);

// const filteredJobs = ref([]);

// const updateJobs = () => {
//   console.log("updateJobs called");
//   if (selectedTags.value.length === 0) {
//     filteredJobs.value = jobs.value;
//     return;
//   }

//   filteredJobs.value = jobs.value.filter((job) => {
//     let jobTagArray = [job.role, job.level, ...job.languages, ...job.tools];

//     let isSelected = false;
//     for (let i = 0; i < jobTagArray.length; i++) {
//       if (selectedTags.value.includes(jobTagArray[i])) {
//         isSelected = true;
//         break;
//       }
//     }
//     return isSelected;
//   });

//   console.log(filteredJobs.value);
// };

// watchEffect(selectedTags, updateJobs);
// updateJobs();

const filteredJobs = computed(() => {
  selectedTags.value;
  jobs.value;

  if (selectedTags.value.length === 0) {
    return jobs.value;
  }

  return jobs.value.filter((job) => {
    console.log(job);
    let jobTagArray = [job.role, job.level, ...job.languages, ...job.tools];

    let isSelected = true;

    for (let i = 0; i < selectedTags.value.length; i++) {
      if (!jobTagArray.includes(selectedTags.value[i])) {
        isSelected = false;
      }
    }

    console.log(isSelected);
    return isSelected;
  });
});

// const updateJobs = (jobs, tags) => {
//   let newjobs = [];

//   if (tags.length === 0) {
//     return jobs;
//   }

//   jobs.forEach((job) => {
//     let jobTags = [job.role, job.level, ...job.languages, ...job.tools];
//     let allTag = true;

//     for (let i = 0; i < tags.length; i++) {
//       if (!jobTags.includes(tags[i])) {
//         allTag = false;
//       }
//     }

//     if (allTag) {
//       newjobs.push(job);
//     }
//   });

//   return newjobs;
// };

const onSelectTag = (val) => {
  if (!selectedTags.value.includes(val)) {
    selectedTags.value.push(val);
    // jobs.value = updateJobs(jsonData.value, tags.value);
  }
};

const onDeselectTag = (val) => {
  if (val === "clearTags") {
    selectedTags.value = [];
  } else {
    selectedTags.value = selectedTags.value.filter(function (item) {
      return item !== val;
    });
  }
};

// jobs.value = updateJobs(jsonData.value, tags.value);
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