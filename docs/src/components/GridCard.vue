<template>
    <div class="card" :style="{ backgroundImage: `linear-gradient(to right, rgba(0,0,0,.7), rgba(0,0,0,0)), url('${require(`@/assets/images/${device}/image-${image}.jpg`)}')` }">
        <p class="card__title" :style="title == 'The Grid' ? { maxWidth: '4ch' } : {}">{{ title }}</p>
    </div>
</template>

<script>
    export default {
        props: {
            title: String,
            image: String,
            device: String
        }
    }
</script>

<style lang="scss" scoped>
@import '@/assets/scss/style.scss';

.card {
    position: relative;
    width: 100%;
    min-height: 8rem;
    background-size: cover;
    display: flex;
    align-items: center;
    padding: 2rem 0 0 1.5rem;
    color: $white;
    cursor: pointer;
    &:after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: transparent;
        opacity: .65;
        transition: all .35s ease;
    }
    &:hover:after {
        background-color: $white;
    }
    &:hover {
        color: $black;
    }
    @include md {
        width: 45%;
    }
    @include xl {
        height: 35rem;
        width: 23.5%;
        align-items: flex-end;
        padding-bottom: 3rem;
    }
    &__title {
        position: relative;
        max-width: 9ch;
        text-transform: uppercase;
        font-size: 1.5rem;
        z-index: 3;
        @include xl {
            font-size: 2rem;
        }
    }
}
</style>