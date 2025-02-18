<template>
  <div>
    <AddHero @hero-added="addHero" />
    <HeroList :heroes="heroes" @hero-selected="selectHero" />
    <HeroDetail v-if="selectedHero" :hero="selectedHero" @updated="updateHero" />
  </div>
</template>

<script>
import HeroList from './components/HeroList.vue';
import HeroDetail from './components/HeroDetail.vue';
import AddHero from './components/AddHero.vue';

export default {
  components: { HeroList, HeroDetail, AddHero },
  data() {
    return {
      heroes: [],
      selectedHero: null
    };
  },
  methods: {
    addHero(hero) {
      this.heroes.push(hero);
    },
    selectHero(hero) {
      this.selectedHero = hero;
    },
    updateHero(updatedHero) {
      const index = this.heroes.findIndex(hero => hero.id === updatedHero.id);
      if (index !== -1) {
        this.$set(this.heroes, index, updatedHero);
      }
    }
  }
};
</script>
