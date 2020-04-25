<template>
    <div class="container">
        <div class="main">
            <div class="pay-title">
                <!-- Number().toFixed(2) 保留2位小数点 -->
                支付总金额 <span class="pay-price">￥ {{ Number(detail.price).toFixed(2) }}</span>
            </div>
            <div class="pay-main">
                <h4>微信支付</h4>
                <el-row type="flex" 
                justify="space-between" 
                align="middle"
                class="pay-qrcode">
                    <div class="qrcode">
                        <!-- 二维码 -->
                        <canvas id="qrcode-stage"></canvas>
                        <p>请使用微信扫一扫</p>
                        <p>扫描二维码支付</p>
                    </div>
                    <div class="pay-example">
                        <img src="http://157.122.54.189:9093/images/wx-sweep2.jpg" alt="">
                    </div>
                </el-row>
            </div>
        </div>
    </div>
</template>

<script>
import QRcode from "qrcode"
export default {
    data(){
        return {
            // 订单详细信息
            detail: {}
        }
    },
    mounted(){
        setTimeout(() => {
            // 请求订单订单详情
            this.$axios({
                url: "/airorders/" + this.$route.query.id,
                headers: {
                    Authorization: `Bearer ` + this.$store.state.user.userInfo.token
                }
            }).then(res => {
                // 主要使用用到价格和支付链接
                this.detail = res.data;
                // 根据文档调用toCanvas方法来生成二维码
                // 文档地址： https://github.com/soldair/node-qrcode#tocanvascanvaselement-text-options-cberror
                const canvas = document.querySelector("#qrcode-stage");
                // 第一个参数canvas节点元素
                // 第二个是生成二维码的链接
                QRcode.toCanvas(canvas, this.detail.payInfo.code_url, {
                    width: 200
                })
            })
        }, 0)
    }
}
</script>

<style scoped lang="less">
.container{
    background:#f5f5f5;
    padding: 30px 0;

    .main{
        width:1000px;
        margin:0 auto;

        .pay-title{
            text-align: right;
            span{
                font-size:28px;
                color:orangered;
            }
        }

        .pay-main{
            background:#fff;
            margin-top:10px;
            border-top: 5px orange solid;
            padding:30px;

            h4{
                font-size: 28px;
                font-weight: normal;
                margin-bottom: 10px;
            }

            .pay-qrcode{
                padding:0 80px;
            }

            .qrcode{
                border:1px #ddd solid;
                padding:15px;
                height: fit-content;

                #qrcode-stage{
                    width:200px;
                    height:200px;
                    margin-bottom: 10px;
                }

                p{
                    line-height: 2;
                    text-align: center;
                }
            }
        }
    }
}
</style>