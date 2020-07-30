<!-- 
 * @FileDescription: 每日新增终端数
 * @Author: 李勇
 * @Date: 2020-07-17    09：29
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div>
        <div class="panel bar1">
            <p>今日新增终端数</p>
            <div class="center">
                <div class="content">       
                    <div class="one"><p></p><span></span></div>
                </div>
                <p class="quantity"><span> 0台</span></p>   
            </div>
            
            <div class="panel-footer"></div>
        </div>
    </div>
</template>
<script>
import echarts from "echarts";

export default {
    methods: {
        terminator(){
           
        },
        
    },
    mounted() {
        
    },
}
</script>
<style lang="scss" scoped>
    .panel {
        position: relative;
        height:3.2rem;
        border: 1px solid rgba(25, 186, 139, 0.17);
        background: rgba(255, 255, 255, 0.04) url("~@/assets/images/line.png");
        padding: 0 0.1875rem 0.5rem;
        margin-bottom: 0.1875rem;
        &::before {
            position: absolute;
            top: 0;
            left: 0;
            content: "";
            width: 10px;
            height: 10px;
            border-top: 2px solid #02a6b5;
            border-left: 2px solid #02a6b5;
        }
        &::after {
            position: absolute;
            top: 0;
            right: 0;
            content: "";
            width: 10px;
            height: 10px;
            border-top: 2px solid #02a6b5;
            border-right: 2px solid #02a6b5;
        }
        .panel-footer {
            position: absolute;
            left: 0;
            bottom: 0;
            width: 100%;
            &::before {
                position: absolute;
                bottom: 0;
                left: 0;
                content: "";
                width: 10px;
                height: 10px;
                border-bottom: 2px solid #02a6b5;
                border-left: 2px solid #02a6b5;
            }
            &::after {
                position: absolute;
                bottom: 0;
                right: 0;
                content: "";
                width: 10px;
                height: 10px;
                border-bottom: 2px solid #02a6b5;
                border-right: 2px solid #02a6b5;
            }
        }

        p{
            height: 0.6rem;
            line-height: 0.6rem;
            text-align: center;
            color: #fff;
            font-size: 0.25rem;
            font-weight: 400;
        }
        #counting{
            height:100%;
        }
    }
    .center{
        display: flex;
        justify-content: center;
        align-items: center;
        margin-top:7%;
    }
    .content div{
        background:transparent;
        width:1.4rem;
        height:1.4rem;
        border: 6px #0cd3db solid;
        border-radius:50%;
        position: relative;
    }

    .content p, .content span{
        position: absolute;
        left: 38%;
        top: 37%;
        width: .3rem;
        height: .3rem;
        border-radius:50%;
        animation: myfirst 2s  infinite;
        box-shadow: 0px 0px 6px #4fadfd; 
        margin: 0px;
    }
    .content  span{
        animation-delay:1s;
    }

    @keyframes myfirst{
        10% {transform: scale(4);}
        100% {transform: scale(7);}
    }
    .quantity{
        position:absolute;
        // left:45.6%;
        // top:44%;
        span{
            color: #4fadfd;
        }
    }
</style>