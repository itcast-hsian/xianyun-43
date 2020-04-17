<template>
    <div>
        <!-- 头部组件 -->
        <Header/>
        <!-- 类似于router-view, 匹配到的组件的坑位 -->
        <nuxt />
    </div>
</template>

<script>
// 导入公共组件
import Header from "@/components/header.vue";

export default {
    components: {
        Header
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
}
ul,
li,
ol {
    list-style: none;
}
a {
    text-decoration: none;
    color: inherit;
}
a:hover {
}
em,
i {
    font-style: normal;
}
</style>
