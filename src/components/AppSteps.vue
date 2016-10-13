<template>
    <main-layouts class="app-steps">
        <div slot="left">
            <el-steps :active="current_step" process-status="finish" finish-status="success">
                <el-step title="框架"></el-step>
                <el-step title="搜索"></el-step>
                <el-step title="CMS"></el-step>
                <el-step title="会员"></el-step>
                <el-step title="支付"></el-step>
                <el-step title="推荐"></el-step>
                <el-step title="订阅"></el-step>
                <el-step title="评论"></el-step>
                <el-step title="设计"></el-step>
            </el-steps>
        </div>
        <div slot="right" class="btn-right">
            <el-button icon="arrow-left" @click.native="prevStep">上一步</el-button>
            <el-button type="primary" @click.native="nextStep">下一步<i class="el-icon-arrow-right el-icon-right"></i></el-button>
        </div>
    </main-layouts>
</template>

<script>
    import MainLayouts from '../layouts/MainLayouts.vue'
    import messageBus from '../utilities/messageBus.js'

    export default {
        components: { MainLayouts },

        data() {
            return {
                current_step: 0,
                step_data: null,
            };
        },

        methods: {
            fetchData(url) {
                this.$http.get(url).then((response) => {
                    this.step_data = response.data;
                    this.notify("step-update", this.step_data[0]);
                }, (response) => {
                    console.log("Get " + url + " error!");
                });
            },

            notify(type, data) {
                messageBus.$emit(type, data);
            },

            nextStep() {
                if ( this.current_step < this.step_data.length - 1) {
                    this.current_step += 1;
                    this.notify("step-update", this.step_data[this.current_step]);
                }
                else if (this.current_step === this.step_data.length - 1) {

                }
                else {

                }
            },

            prevStep() {
                if( this.current_step > 0) {
                    this.current_step -= 1;
                    this.notify("step-update", this.step_data[this.current_step]);
                }
                else {

                }
            },
        },
        mounted() {
            this.fetchData('/assets/step_data.json');
        },
    }

</script>

<style>
    .app-steps {
        margin-top: 3rem;
    }
    
    .btn-right {
        float: right;
    }

    .btn-right .el-button:not(:last-child) {
        margin-right: 10px;
    }

</style>
