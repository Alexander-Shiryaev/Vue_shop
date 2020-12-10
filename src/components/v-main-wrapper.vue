<template>
    <div class="v-main-wrapper">
        <keep-alive>
            <router-view></router-view> 
        </keep-alive>
    <v-form />
    </div>
</template>

<script>
    import vForm from "./v-form.vue";

    export default {
        name: "v-main-wrapper",
        components: {
            vForm,
        },
        props: {},
        data() {
            return {
                title: 'Main wrapper'
            }
        },
        computed: {},
        methods: {},
        watch: {}
    }
</script>

<style>
    .v-main-wrapper {
        max-width: 900px;
        margin: 0 auto;
    }
</style>