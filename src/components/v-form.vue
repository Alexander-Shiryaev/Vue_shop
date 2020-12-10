<template>
    <form class="v-form">
        <h1 class="v-form__title">Заказать обратный звонок</h1>
        <input class="v-form__input v-form__name" data-rule="text" type="text" placeholder="Ваше имя">
        <input class="v-form__input v-form__phone" data-rule="tel" type="tel" placeholder="Ваш телефон">
        <input class="v-form__input v-form__email" data-rule="email" type="email" placeholder="Email">
        <button class="v-form__btn btn" type="submit">Связаться с нами</button>
    </form>
</template>

<script>

    export default {
        name: "v-form",
        props: {},
        data() {
            return {}
        },
        computed: {},
        methods: {},
        watch: {}
    }
</script>

<style lang="scss">
.v-form {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 0;
    &__input {
        outline: none;
        font-size: 16px;
        border: none;
        border-bottom: 1px solid $bg-color;
    }
    &__name, &__phone, &__email {
        display: block;
        padding: $padding*2;
        width: 600px;
        margin: 15px auto;
    }
    &__email {
        margin:  15px auto 40px;
    }
    &__btn {
        font-size: 16px;
    }
}
</style>