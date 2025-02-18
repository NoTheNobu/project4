<template>
    <div>
      <h2>Hero List</h2>
      <ul>
        <li v-for="hero in heroes" :key="hero.id">
          {{ hero.name }} - {{ hero.playtime }} hours
          <button @click="selectHero(hero)">Details</button>
        </li>
      </ul>
      <p>Total Playtime: {{ totalPlaytime }} hours</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['heroes'],
    computed: {
      totalPlaytime() {
        return this.heroes.reduce((total, hero) => total + hero.playtime, 0);
      }
    },
    methods: {
      selectHero(hero) {
        this.$emit('hero-selected', hero);
      }
    }
  };
  </script>
  