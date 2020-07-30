<!-- 
 * @FileDescription:终端页面
 * @Author: 李勇
 * @Date: 2020-07-21    15：21
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <!-- 
        xs < 768apx
        sm ≥ 768px 
        md ≥ 992px
        lg ≥ 1200px
        xl≥ 1920px
     -->
    <div class="terminal_box">
        <el-row :gutter="10">
            <el-col :xs="24" :lg="7" :xl="7">
                <div class="panel">
                    <Demolished />
                    <Terminus />
                    <div class="panel-footer"></div>
                </div>
                
            </el-col>
            <el-col :xs="24" :lg="10" :xl="10">
                <!-- <Wander />  -->
                <Province />
            </el-col>
            <el-col :xs="24" :lg="7" :xl="7">
                <div class="panel">
                    <Disjunctor />
                    <Proportionofquantity />
                    <div class="panel-footer"></div>
                </div>
            </el-col>
        </el-row>
        <el-row :gutter="10">
            <el-col :xs="24" :lg="7" :xl="7">
                <div class="panel">
                    <OnlineRate />
                    <div class="panel-footer"></div>
                </div>
                
            </el-col>
            <el-col :xs="24" :lg="10" :xl="10">
                <div class="panel">
                    <FractureRate />
                    <div class="panel-footer"></div>
                </div>
                
            </el-col>
            <el-col :xs="24" :lg="7" :xl="7">
                <div class="panel">
                    <DeviceRatio />
                    <div class="panel-footer"></div>
                </div>
                
            </el-col>
        </el-row>
    </div>
</template>
<script>
import {Demolished,Terminus} from "@/views/terminal/components/leftEquipment/index.js";
import Wander from "@/views/terminal/components/Wander.vue";
//流向图
import Province from "@/views/terminal/components/Province.vue";
import {Disjunctor,Proportionofquantity} from "@/views/terminal/components/rightEquipment/index.js";
import OnlineRate from "@/views/terminal/components/OnlineRate.vue";
import FractureRate from "@/views/terminal/components/FractureRate.vue";
import DeviceRatio from "@/views/terminal/components/DeviceRatio.vue";
export default {
    components:{
        Demolished,
        Terminus,
        Wander,
        Province,
        Disjunctor,
        Proportionofquantity,
        OnlineRate,
        FractureRate,
        DeviceRatio

    }
}
</script>
<style lang="scss" scoped>
    @import "@/styles/item.scss";
    .terminal_box{
        width:100%;
        min-height: calc(100vh - 50px);
        box-sizing:border-box;
        background: url("~@/assets/images/two.jpg") no-repeat #000;
        background-size: cover;
        padding:0.16rem 0.16rem 0rem 0.16rem;
    }
</style>