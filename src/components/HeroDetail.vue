<template>
    <div v-if="hero">
      <h2>{{ hero.name }}</h2>
      <p>Playtime: {{ hero.playtime }} hours</p>
      <button @click="updatePlaytime">Update Playtime</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['hero'],
    methods: {
      updatePlaytime() {
        const newPlaytime = prompt("Enter new playtime:");
        if (newPlaytime) {
          this.hero.playtime = parseInt(newPlaytime);
          this.$emit('updated', this.hero);
        }
      }
    }
  };
  </script>
  