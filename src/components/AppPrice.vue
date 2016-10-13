<template>
    <el-table :data="select_data" stripe>
        <el-table-column property="name" label="组件"></el-table-column>
        <el-table-column property="select" label="选择"></el-table-column>
        <el-table-column property="price" label="价格"></el-table-column>
    </el-table>
</template>

<script>
    export default {
        data() {
            return {
                select_data: []
            }
        }
    }
</script>
