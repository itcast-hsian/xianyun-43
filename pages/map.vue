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

        // 1.默认的，创建一个 Marker 实例：
        var marker = new AMap.Marker({
            position: new AMap.LngLat(113.3245904, 23.1066805),   // 经纬度对象，也可以是经纬度构成的一维数组[116.39, 39.9]
            title: '广州塔'
        });

        // 2.通过自定义图片，创建 AMap.Icon 实例：
        var icon = new AMap.Icon({
            size: new AMap.Size(40, 40),    // 图标尺寸
            image: '/images/QQ图片20200426142514.jpg',  // Icon的图像
            // imageOffset: new AMap.Pixel(0, -60),  // 图像相对展示区域的偏移量，适于雪碧图等
            imageSize: new AMap.Size(40, 40)   // 根据所设置的大小拉伸或压缩图片
        });

        // 创建一个 Marker 实例：
        var marker2 = new AMap.Marker({
            position: new AMap.LngLat(113.191098, 23.081027),   // 经纬度对象，也可以是经纬度构成的一维数组[116.39, 39.9]
            title: '东航同学',
            // 自定义图标
            icon: icon
        });

        // 3.自定内容
        var content = `<div style="
        width:40px; 
        height: 40px; 
        background: url('/images/QQ图片20200426142514.jpg');
        border-radius: 50%;
        background-size: 100%">
        </div>`;

        var marker3 = new AMap.Marker({
            content: content,  // 自定义点标记覆盖物内容
            position:  [113.3545904, 23.1066805], // 基点位置
            offset: new AMap.Pixel(-17, -42) // 相对于基点的偏移位置
        });

        // 将创建的点标记添加到已有的地图实例：
        map.add([marker, marker2, marker3]);
    }
};
</script>

<style scoped>
#container {width:500px; height: 500px; } 
</style>