<template>
  <div id="app">
    <AppHeader 
    :genres="mainGenreList"
    @selectedValue="getValue"
    @resetValue="resetValue"
    :authors="mainAuthorsList"
    @authorsOptionValue="getAuthorsOptionValue"
    @resetAuthorValue="resetAuthorValue"/>
    
    <AppMain 
    @genreList="getGenresFromMain"
    @selectedValue="getValue"
    :value="optionValue"
    @authorsList="getAuthorsFromMain"
    :authorsValue="authorsOptionValue"/>
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
      optionValue: null,
      mainAuthorsList: [],
      authorsOptionValue: null
    }
  },
  methods: {
    getGenresFromMain(mainGenre) {
      this.mainGenreList = mainGenre;
    },
    getValue(value) {
      this.optionValue = value;
    },
    resetValue(value) {
      this.optionValue = value;
    },
    getAuthorsFromMain(mainAuthors) {
      this.mainAuthorsList = mainAuthors;
    },
    getAuthorsOptionValue(authorsOptionValue) {
      this.authorsOptionValue = authorsOptionValue;
    },
    resetAuthorValue(authorValue) {
      this.authorsOptionValue = authorValue;
    }
  }
}
</script>

<style lang="scss">
  @import './styles/general.scss';
</style>
