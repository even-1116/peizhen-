<script setup>
import TreeMenu from './treeMenu.vue'
import {useRouter} from 'vue-router'
import {reactive,computed} from 'vue'
import  {useStore} from 'vuex'

const store = useStore()
const isCollapse = computed(()=>store.state.menu.isCollapse)

const handleOpen = () =>{}
const handleClose = () =>{}

const active = computed(() => store.state.menu.menuActive)

const router = useRouter()
const menuData = reactive(router.options.routes[0].children)
// console.log(router,'router');

</script>

<template>
    <el-menu
        :style="{width: !isCollapse ?  '230px' : '64px'}"
        active-text-color="#ffd04b"
        background-color="#545c64"
        class="el-menu-vertical-demo"
        text-color="#fff"
        @open="handleOpen"
        @close="handleClose"
        :collapse="isCollapse"
        :default-active="active"
      >
        <p class="logo-lg">{{!isCollapse ? 'EVEN陪诊' : 'EVEN'}}</p>
        <TreeMenu :menuData="menuData" :index="1"></TreeMenu>
    </el-menu>
</template>

<style lang="less" scoped>
.el-menu-vertical-demo{
    height: 100%;
    .logo-lg{
        font-size: 20px;
        text-align: center;
        height: 50px;
        line-height: 50px;
        color: #fff
    }
}
</style>