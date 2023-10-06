<script>
import { defineComponent } from 'vue'; 

export default defineComponent({
  props: ["current"],
  setup(props, { emit }) {
    // Define filterBy method 
    const filterBy = (value) => {
      emit("filterValue", value);
    };

    // Return filterBy method
    return {
      filterBy,
    };
  },
});
</script>

<template>
    <nav class="filterBar">
        <button @click="filterBy('all')" :class="{ active:current === 'all'}">All</button>
        <button @click="filterBy('ongoing')" :class="{ active:current === 'ongoing'}">Ongoing</button>
        <button @click="filterBy('complete')" :class="{ active:current === 'complete'}">Complete</button>
    </nav>
</template>



<style>
.filterBar{
    color: #bbb;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    letter-spacing: 1px;
    font-weight: bold;

}
button{
    background: none;
    color: #bbb;
    font-size: 12px;
    text-transform: uppercase;
    margin-right: 10px;
    letter-spacing: 1px;
    font-weight: bold;
    cursor: pointer;
    padding: 4px;
    margin-bottom: 10px;
}
button.active{
    color: rgb(22, 222, 155);
}
</style>