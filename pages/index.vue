<template>
    <div>
        <!-- el-carousel 轮播图组件 -->
        <el-carousel height="700px" style="min-width: 1000px;">
            <!-- 要循环的轮播图的每一项 -->
            <el-carousel-item v-for="item in 4" :key="item">
                <!-- 图片img标签不能实现居中对齐，可以使用背景图片 -->
                <div :style="`
                    background: url(http://157.122.54.189:9095/assets/images/th02.jfif) center top no-repeat;
                    height: 700px;
                `"></div>
            </el-carousel-item>
        </el-carousel>
    </div>
</template>

<script>
export default {

};
</script>

<style scoped lang="less">

</style>