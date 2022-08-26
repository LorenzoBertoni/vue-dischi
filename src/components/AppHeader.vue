<template>
    <header>
        <div class="logo">
            <img src="https://grafica-facile.com/wp-content/uploads/2022/01/spotify-logo.png" alt="Spotify Logo">
        </div>
    </header>
</template>

<script>
export default {
    name: 'AppHeader'
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
    }
</style>