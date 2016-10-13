<template>
    <article class="markdown-page" v-html="compiledHtml" ></article>
</template>

<script>
    import marked from 'marked'
    export default {
        props: ['RawMd'],
        computed: {
            compiledHtml() {
                return marked(this.RawMd, { sanitize: true })
            }
        }
    }
</script>

<style>
    .markdown-page h2 {
        margin: 0;
        font-size: 16px;
        color: #475669;
    }

    .markdown-page h2:not(:first-child) {
        margin-top: 2rem;
    }

    .markdown-page h4 {
        margin: 0;
        font-size: 14px;
        font-style:italic;
        color: #8492A6;
    }

    .markdown-page ul {
        margin: 0;
    }

    .markdown-page p {
        margin: 0;
        font-size: 14px;
    }

    .markdown-page p em {
        font-size: 14px;
    }

    .markdown-page p img {
        max-width: 75%;
        height: auto;
        margin: 1rem 0 0;
    }
</style>