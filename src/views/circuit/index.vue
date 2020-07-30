<!-- 
 * @FileDescription:线路页面
 * @Author: 李勇
 * @Date: 2020-07-23    09：30
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div class="line line_big">
        <!-- 
            xs < 768px
            sm ≥ 768px 
            md ≥ 992px
            lg ≥ 1200px
            xl≥ 1920px
         -->
        <div class="line_left"> 
            <div class="panel">
                <h2 style="color:#fff">在产企业占比</h2>
                <div class="all_line">
                    <LineTotal />
                    <LineNewly />
                </div>
                <div class="panel-footer"></div>
            </div>
            <div class="line_top">
                <LineTop />
            </div>
        </div>
        <div class="line_right">
            <div class="line_tree panel">
                <LineRegion />
                <div class="panel-footer"></div>
            </div>
            <div class="line_table">
                <LineTable />
            </div>
        </div>
    </div>
</template>
<script>
import {LineTotal,LineNewly} from "@/views/circuit/components/lineSituation/index.js";
import LineRegion from "@/views/circuit/components/LineRegion.vue";
import LineTop from "@/views/circuit/components/LineTop.vue";
import LineTable from "@/views/circuit/components/LineTable.vue";
export default {
    components:{
        LineTotal,
        LineNewly,
        LineRegion,
        LineTop,
        LineTable
    }
}
</script>
<style lang="scss" scoped>
    @import "@/styles/item.scss";
    //较大的放前，较小的放后 
    // min-width: 大于等于
    // max-width:  小于等于
    .line_big{
        width:100%;
        // 最大时这些
        min-height: calc(100vh - 50px);
        box-sizing:border-box;
        background: url("~@/assets/images/two.jpg") no-repeat #000;
        background-size: cover;
        padding:0.16rem 0.16rem 0rem 0.16rem;
    }
    @media screen and (min-width:1200px) {
        .line{
            min-height: calc(100vh - 50px);
            display:flex;
            width:100%;
            .line_left{
                flex:2;    
            }
            .line_right{
                flex:4;
            }
        }
        .line_tree{
            margin-left:.2rem;
        }
    }
    @media screen and (max-width:1200px) and(min-width:992px) {//
        .line{
            min-height: calc(100vh - 50px);
            display:flex;
            width:100%;
            .line_left{
                flex:2;
            }
            .line_right{
                flex:4;
            }
        }
        .line_tree{
            margin-left:.2rem;
        }
    }
    @media screen and (max-width:992px) and(min-width:768px) {//
        .line{
            min-height: calc(100vh - 50px);
            display:flex;
            width:100%;
            .line_left{
                flex:1;
            }
            .line_right{
                flex:3;
            }
        }
        .line_tree{
            margin-left:.2rem;
        }
    }
    @media screen and (max-width:768px) {
        .line{
            min-height: calc(100vh - 50px);
            width:100%;
        }
    }
    .all_line{
        display: flex;
    }
    .line_top{
        margin-top:.1rem;
    }
    .line_table{
        margin-top:.2rem;
    }
    
</style>