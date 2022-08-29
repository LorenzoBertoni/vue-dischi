<template>
    <div class="card">
                <div class="card-img">
                    <img :src="disc.poster" :alt="disc.title">
                </div>

                <div class="card-title">
                    <h3>{{disc.title.toUpperCase()}}</h3>
                </div>

                <div class="card-text">
                    <div class="author">
                        {{disc.author}}
                    </div>

                    <div class="release">
                        {{disc.year}}
                    </div>
                </div>
            </div>
</template>

<script>
export default {
    name: 'SingleCard',
    props: {
        disc: Object
    },
    mounted() {
        this.$emit('discsGenres', this.disc.genre);
    }
}
</script>

<style scoped lang="scss">
@import '../styles/vars.scss';

    .card {
        width: calc(20% - 2rem);
        background-color: $card_color;

        .card-img {
            width: 70%;
            height: 130px;
            margin: 1.5rem auto;
            cursor: pointer;
            transition: transform linear .2s;

            &:hover {
                transform: scale(1.1);
            }
            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
                object-position: center;
                display: block;
            }
        }

        .card-title {
            color: #fff;
            text-align: center;
            font-size: 1rem;
            padding: 1rem;
            cursor: pointer;

            h3 {
                word-wrap: break-word;

                &:hover {
                    text-decoration: underline;
                }
            }
        }

        .card-text {
            margin: 1rem 0 3rem 0;

            .author, .release {
                color: gray;
                font-weight: 600;
                margin-top: .2rem;
                text-align: center;
            }
        }
    }
</style>