<template>
    <div id="app">
        <app-menu></app-menu>
        <app-steps></app-steps>
        <main-layouts class="app-content">
            <app-form slot="left"></app-form>
            <app-price slot="right"></app-price>
        </main-layouts>
    </div>
</template>

<script>
    import MainLayouts from './layouts/MainLayouts.vue'
    import AppMenu from './components/AppMenu.vue'
    import AppSteps from './components/AppSteps.vue'
    import AppForm from './components/AppForm.vue'
    import AppPrice from './components/AppPrice.vue'

    export default {
        components: { MainLayouts, AppMenu, AppSteps, AppForm, AppPrice },
    }
</script>

<style>

    html, body {
        margin: 0;
        padding: 0;
        height: 100%;
    }

    body {
        font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
        -webkit-font-smoothing: antialiased;
        min-width: 1024px;
    }

    .container {
        margin-left: 3rem;
        margin-right: 3rem;
    }

    .app-content {
        margin-top: 3rem;
    }

</style>