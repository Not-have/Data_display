<!-- 
 * @FileDescription:获取当前时间 ：年月日时分秒
 * @Author: 李勇
 * @Date: 2020-07-16    13：32
 * @LastEditors: 李勇
 * @LastEditTime: 2020-07-27  20：44
 -->
<template>
    <div class="current_box">
        <!-- <iframe src="/html/index.html" class="neiqian"></iframe> -->
        <h1>数据</h1>
        <div class="showTime">{{nowTime}}</div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            nowTime:null
        }
    },
    methods: {
        time(){
            let t = null;
            t = setTimeout(time, 1000); //開始运行
            function time() {
                clearTimeout(t); //清除定时器
                let dt = new Date();
                let y = dt.getFullYear();
                let mt = dt.getMonth() + 1;
                let day = dt.getDate();
                let h = dt.getHours(); //获取时
                let m = dt.getMinutes(); //获取分
                let s = dt.getSeconds(); //获取秒
                document.querySelector(".showTime").innerHTML =
                    "当前时间：" +
                    y +
                    "年" +
                    mt +
                    "月" +
                    day +
                    "日" +
                    h +
                    "时" +
                    m +
                    "分" +
                    s +
                    "秒";
                t = setTimeout(time, 1000); //设定定时器，循环运行
            }
        }
    },
    mounted() {
        this.time();
    },
    created() {
        
    },
}
</script>
<style lang="scss" scoped>
    .current_box{
        background:#09143d;
        height:1rem;
        color: white;
        position: relative;
        background: url("~@/assets/images/head_bg.png") no-repeat top center;
        background-size: 100% 100%;
        h1{
            text-align: center;
            font-size:.3rem;
            line-height:.88rem;
        }
        .showTime{
            position:absolute;
            top:.3rem;
            right:.3rem;
            font-size:.2rem;
        }
    }
    @media screen and(max-width:768px) {
        .current_box{
            background:#09143d;
            height:1rem;
            color: white;
            position: relative;
            background: url("~@/assets/images/head_bg.png") no-repeat top center;
            background-size: 100% 100%;
            h1{
                text-align: center;
                font-size:.3rem;
                line-height:.9rem;
            }
        }
        .showTime{
            display:none;
        }
    }
</style>