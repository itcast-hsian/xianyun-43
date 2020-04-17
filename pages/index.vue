<template>
    <div>
        <!-- el-carousel 轮播图组件 -->
        <el-carousel height="700px" style="min-width: 1000px;">
            <!-- 要循环的轮播图的每一项 -->
            <el-carousel-item v-for="(item, index) in banners" :key="index">
                <!-- 图片img标签不能实现居中对齐，可以使用背景图片 -->
                <div :style="`
                    background: url(${$axios.defaults.baseURL + item.url}) center center no-repeat;
                    height: 700px;
                `"></div>
            </el-carousel-item>
        </el-carousel>
    </div>
</template>

<script>
export default {
    data(){
        return {
            // 存放轮播图
            banners: []
        }
    },
    mounted(){
        // 请求轮播图数据
        this.$axios({
            url: "/scenics/banners"
        }).then(res => {
            // data是轮播图的数组
            const {data} = res.data;
            // 保存到data中
            this.banners = data;
        })
    }
};
</script>

<style scoped lang="less">

</style>