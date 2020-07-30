<!-- 
 * @FileDescription:故障页面
 * @Author: 李勇
 * @Date: 2020-07-20    15：30
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div class="from">
        <!-- 
            xs < 768apx
            sm ≥ 768px 
            md ≥ 992px
            lg ≥ 1200px
            xl≥ 1920px
         -->
        <el-row :gutter="10">
            <el-col :xl="7" :md="7" :xs="24">
                <MounthlyFailure />
            </el-col>
            <el-col :xl="10" :md="10" :xs="24">
                <YearsFailure /> 
            </el-col>
            <el-col :xl="7" :md="7" :xs="24">
                <ZoneFault />
            </el-col>
        </el-row>
        <el-row :gutter="10" class="fault_two">
            <el-col :xl="7" :md="7" :xs="24">
                <div class="panel">
                    <WeekFailure />
                    <AnnularFailure />
                    <div class="panel-footer"></div>
                </div>
            </el-col>
            <el-col :xl="10" :md="10" :xs="24">
                <YearlyFailure />
            </el-col>
            <el-col :xl="7" :md="7" :xs="24">
                <RoundFold />
            </el-col>
        </el-row>
    </div>
</template>
<script>
import MounthlyFailure from "@/views/form/components/MonthlyFailure.vue";
import YearsFailure from "@/views/form/components/YearsFailure.vue";
import ZoneFault from "@/views/form/components/ZoneFault.vue";
import {WeekFailure,AnnularFailure} from "@/views/form/components/circuit/index.js";
import YearlyFailure from "@/views/form/components/YearlyFailure.vue";
import RoundFold from "@/views/form/components/RoundFold.vue";
export default {
    components:{
        MounthlyFailure,
        YearsFailure,
        ZoneFault,
        WeekFailure,
        AnnularFailure,
        YearlyFailure,
        RoundFold
    }
}
</script>
<style lang="scss" scoped>
    @import "@/styles/item.scss";
    .from{
        width:100%;
        // 最大时这些
        min-height: calc(100vh - 50px);
        box-sizing:border-box;
        background: url("~@/assets/images/bg.jpg") no-repeat #000;
        background-size: cover;
        padding:0.16rem 0.16rem 0rem 0.16rem;
    }


</style>