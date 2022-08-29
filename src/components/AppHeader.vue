<template>
    <header>
        <a href="#" class="logo">
            <img src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt="Spotify Logo">
        </a>

        <select 
        name="select-genre" id="select-genre" 
        v-model="optionValue" 
        @change="$emit('selectedValue', optionValue)"
        >
            <option v-for="(genre, index) in getFilteredList()"
            :key="index"
            :value="genre"
            >
            {{genre}}</option>
        </select>   

        <button 
        id="reset" 
        @click="reset"
        >
        Reset</button>
    </header>
</template>

<script>
export default {
    name: 'AppHeader',
    props: {
        genres: Array
    },
    data() {
        return {
            optionValue: null
        }
    },
    methods: {
        getFilteredList() {
            let filteredGenre = [];

            this.genres.forEach(genre => {
                if(!filteredGenre.includes(genre)) {
                    filteredGenre.push(genre);
                }
            })

            return filteredGenre;
        },
        reset() {
            this.optionValue = null;
            this.$emit('resetValue', this.optionValue);
        }
    }
}
</script>

<style scoped lang="scss">
@import '../styles/vars.scss';

    header {
        width: 100%;
        padding: 1rem;
        background-color: $header_color;
        display: flex;
        justify-content: flex-start;
        align-items: center;

        .logo {
            width: 50px;
            height: 50px;
            margin-left: 1rem;

            img {
                width: 100%;
                height: 100%;
            }
        }

        #select-genre, #reset {
            padding: .5rem 1rem;
            border: none;
            border-radius: .5rem;
            margin: 1rem;
            font-size: 1.1rem;
        }
    }
</style>