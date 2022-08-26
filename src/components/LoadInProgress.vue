<template>
    <div class="load-in-progress">
        <h1>Load In Progress...</h1>
    </div>
</template>

<script>
export default {
    name: 'LoadInProgress'
}
</script>

<style scoped lang="scss">
    .load-in-progress {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>