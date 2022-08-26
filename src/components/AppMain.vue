<template>
    <main>
        <div class="cards">
            <LoadInProgress v-if="IsLoading"/>
            <SingleCard v-for="(disc, index) in discs.response" :key="index" :disc="disc"/>
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
    created() {
        this.getDiscs();
    },
    data() {
        return {
            discs: [],
            IsLoading: true
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
        }
    }
}
</script>

<style scoped lang="scss">
@import '../styles/vars.scss';

    main {
        width: 100%;
        background-color: $main_color;
        padding: 2.5rem 0 1.6rem 0;

        .cards {
            width: 60%;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            gap: 2rem;    
        }
    }
</style>