<script>
import { ref, reactive, computed, onMounted } from 'vue';

import FilterBar from '../components/FilterBar.vue';
import SingleProject from '../components/SingleProject.vue';
import Description from '../components/Description.vue';

export default {
  name: 'HomeView',
  components: {
    FilterBar,
    SingleProject,
    Description
  },
  setup() {
    // Replace data with ref and reactive
    const projects = ref([]);
    const current = ref('all');

    function delpj(pjId) {
      projects.value = projects.value.filter(project => pjId !== project.id);
    }

    function completepj(completeId) {
      const findpj = projects.value.find(project => project.id === completeId);
      if (findpj) {
        findpj.complete = !findpj.complete;
      }
    }

    // Use onMounted for fetching data
    onMounted(() => {
      fetch('http://localhost:3000/projects')
        .then(response => response.json())
        .then(datas => {
          projects.value = datas;
        })
        .catch(() => {});
    });

    const filteredPj = computed(() => {
      if (current.value === 'ongoing') {
        return projects.value.filter(pj => !pj.complete);
      }
      if (current.value === 'complete') {
        return projects.value.filter(pj => pj.complete);
      }
      return projects.value;
    });

    return {
      projects,
      current,
      delpj,
      completepj,
      filteredPj
    };
  }
};
</script>


<template>
  <div class="home">
    <h1>Home</h1>
    <FilterBar @filterValue = "current=$event" :current = "current"></FilterBar>
    <div v-for="project in filteredPj" :key="project.id" >
      <SingleProject :project="project" @delete = "delpj" @complete="completepj"></SingleProject>
    </div>
    <Description></Description>
  </div>
  <!-- {{ current }} -->
  </template>



<style>
h1{
  font-weight: bold;
  padding-bottom: 20px;
}
</style>
