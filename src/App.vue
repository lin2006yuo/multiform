<template>
    <div id="app">
        <el-breadcrumb separator="/">
            <el-breadcrumb-item>主页</el-breadcrumb-item>
            <el-breadcrumb-item>某表单页</el-breadcrumb-item>
        </el-breadcrumb>
        <main class="ct-wrap">
            <div class="ct">
                <div class="basic-info ct-form" v-for="(config, configIndex) in formConfig" :key="configIndex">
                    <edit-form
                        :config="config"
                        :data="formData"
                        :options="formOptions">
                    </edit-form>
                </div>
            </div>
        </main>
    </div>
</template>

<script>
import API from './api';
import editForm from './edit-form.vue';
export default {
    name: 'app',
    data() {
        return {
            formOptions: {},
            formConfig: [],
            formData: {},
            msg: 'Welcome to Your Vue.js App'
        }
    },
    methods: {},
    created () {
        API.getFormConfigData()
        .then((d) => {
            this.formOptions = d.formOptions;
            this.formConfig = d.formConfig;
            this.formData = d.formData;
        });
    },
    components: {
        editForm
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 60px auto;
}
.ct-wrap {
    position: relative;
    margin-top: 64px;
}
.ct {
    width: 1110px;
    margin: 0 auto;
    border: 1px solid #BFBFBF;
    padding: 56px 40px 40px;
    box-sizing: border-box;
}
.ct-form {
    margin-bottom: 48px;
}
.form__title {
    margin-bottom: 32px;
    font-size: 16px;
    font-weight: bold;
    line-height: 1;
}
.form-content {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.form-content .el-form-item {
    width: 440px;
}
.form-content .el-input {
    width: 194px;
}
.form-content .el-form-item.form-item--full {
    width: 100%;
}
.form-content .form-item-unit--full {
    width: 696px;
}
</style>