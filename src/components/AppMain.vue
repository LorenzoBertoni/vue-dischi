<template>
    <main>
        <div class="cards">
            <LoadInProgress v-if="IsLoading"/>
            
            <SingleCard v-for="(disc, index) in filteredList()"
            :key="index"
            :disc="disc"
            @discsGenres="getDiscsGenres"
            @discAuthors="getDiscsAuthors"
            />
        </div>
    </main>
</template>

<script>
import axios from 'axios';
import SingleCard from './SingleCard.vue';
import LoadInProgress from './LoadInProgress.vue';

export default {
    name: 'AppMain',
    components: {
        SingleCard,
        LoadInProgress
    },
    props: {
        value: String,
        authorsValue: String
    },
    created() {
        this.getDiscs();
    },
    data() {
        return {
            discs: [],
            IsLoading: true,
            genreList: [],
            optionValue: null,
            authorsList: []
        }
    },
    methods: {
        getDiscs() {
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(response => {
                this.discs = response.data;
                this.IsLoading = false;
            })
            .catch(error => {
                console.log(error);
                this.IsLoading = false;
            })
        },
        getDiscsGenres(genre) {
            this.genreList.push(genre);
        },
        filteredList() { //* funzione principale, 
                        //*responsabile della visualizazione
                        //*dinamica degli album in base ai criteri di ricerca 
            if(this.value == null && this.authorsValue == null) {
                return this.discs.response;
            } else {
                const filteredDiscs = this.discs.response.filter(disc => {
                    if(disc.genre == this.value || disc.author == this.authorsValue) {
                        return true;
                    }else {
                        return false;
                    }
                })

                return filteredDiscs;
            }
        },
        getDiscsAuthors(author) {
            this.authorsList.push(author);
        }
    },
    mounted() {
        this.$emit('genreList', this.genreList);
        this.$emit('authorsList', this.authorsList);
    }
}
</script>

<style scoped lang="scss">
@import '../styles/vars.scss';

    main {
        width: 100%;
        height: 100%;
        padding: 2.5rem;

        .cards {
            width: 60%;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            gap: 2rem;    
        }
    }
</style>