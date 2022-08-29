<template>
  <div id="app">
    <AppHeader 
    :genres="mainGenreList"
    @selectedValue="getValue"
    @resetValue="resetValue"
    />
    
    <AppMain 
    @genreList="getDiscsGenresFromMain"
    @selectedValue="getValue"
    :value="optionValue"
    />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';


export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      mainGenreList: [],
      optionValue: null
    }
  },
  methods: {
    getDiscsGenresFromMain(mainGenre) {
      this.mainGenreList = mainGenre;
    },
    getValue(value) {
      this.optionValue = value;
    },
    resetValue(value) {
      this.optionValue = value;
    }
  }
}
</script>

<style lang="scss">
  @import './styles/general.scss';
</style>
