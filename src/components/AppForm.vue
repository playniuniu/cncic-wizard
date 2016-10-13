<template>
    <div class="app-form">
        <el-form :model="form_select" label-position="left" label-width="80px">
            <el-form-item label="组件名称">
                <h1 class="title">{{ form_data.name }}</h1>
            </el-form-item>

            <el-form-item label="组件选项">
                <el-radio-group v-model="form_select.option">
                    <el-radio v-for="el of form_data.options" 
                              :label="el.key"
                              @click.native="fetchDesc(el.desc)"
                    >
                        {{ el.key }}
                    </el-radio>
                </el-radio-group>
            </el-form-item>

            <el-form-item label="选项说明">
                <markdown-page :raw-md="markdown_data"></markdown-page>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    import MarkdownPage from './MarkdownPage.vue'
    import messageBus from '../utilities/messageBus.js'

    export default {
        components: { MarkdownPage },
        data() {
            return {
                form_select: { option: '' },
                form_data: { name: '', options: []},
                markdown_data: "*请选择相应选项*",
            }
        },
        methods: {
            fetchDesc(url) {
                this.$http.get(url).then((response) => {
                    this.markdown_data = response.body;
                }, (response) => {
                    console.log("Get "+ url + " error!");
                });
            },

            initListenMsg() {
                messageBus.$on('step-update', (data) => {
                    this.form_data = data;
                    this.markdown_data = "*请选择相应选项*";
                });
            },
        },
        mounted() {
            this.initListenMsg();
        }
    }
</script>

<style>
    .app-form {
        padding-right: 2rem;
        border-right: 1px solid #C0CCDA;
        color: #8492A6;
    }

    h1.title {
        margin: 0;
        font-size: 20px;
        color: #1F2D3D;
    }
</style>