<template>
    <transition name="fade">
        <slot />
    </transition>
</template>

<script>
    export default {
        name: 'FadeTransition'
    }
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
    transition: opacity .3s;
}

.fade-enter,
.fade-leave-to {
    opacity: 0;
}
</style>
