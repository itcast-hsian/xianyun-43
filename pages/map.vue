<template>
    <div style="width: 1000px; margin: 0 auto; padding: 50px 0;">

        <script 
        type="text/javascript" 
        src="https://webapi.amap.com/maps?v=1.4.15&key=44efad7f524a368a34f95c1855d6fc33"></script>

        <h2>高德地图</h2>

        <div id="container"></div> 

    </div>
</template>

<script>
export default {
    mounted(){
        // Amap在模板中导入js文件之后就应经是一个全局变量了
        // map是一个地图的对象
        var map = new AMap.Map('container', {
            zoom:11,//级别
            center: [113.3245904, 23.1066805],//中心点坐标
        });
    }
};
</script>

<style scoped>
#container {width:500px; height: 500px; } 
</style>