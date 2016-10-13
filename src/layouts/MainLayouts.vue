<template>
    <div class="container">
        <el-row :gutter="40">
            <el-col :span="18">
                <slot name="left"></slot>
            </el-col>
            <el-col :span="6">
                <slot name="right"></slot>
            </el-col>
        </el-row>
    </div>
</template>