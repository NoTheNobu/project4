<template>
    <div>
      <h2>Add Hero</h2>
      <input v-model="heroName" placeholder="Hero Name" />
      <input v-model="playtime" type="number" placeholder="Playtime (hours)" />
      <button @click="addHero">Add Hero</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        heroName: '',
        playtime: 0
      };
    },
    methods: {
      addHero() {
        if (this.heroName && this.playtime >= 0) {
          this.$emit('hero-added', { name: this.heroName, playtime: parseInt(this.playtime), id: Date.now() });
          this.heroName = '';
          this.playtime = 0;
        }
      }
    }
  };
  </script>
  