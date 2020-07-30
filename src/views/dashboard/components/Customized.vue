<!-- 
 * @FileDescription: 本月故障占比的饼状图
 * @Author: 李勇
 * @Date: 2020-07-16    16:28
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div class="panel">
        <h2>本月故障占比</h2>
        <div id="customized">
            
        </div>
        <div class="panel-footer"></div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created() {
        this.$nextTick(()=>{
            this.custom();
        })
    },
    methods: {
        custom(){
            // 基于准备好的dom，初始化echarts实例
            let myChart = echarts.init(document.getElementById('customized'));
            // 指定图表的配置项和数据
            let option = {
                // 这个里面指定图标的样式和数据
                tooltip: {
                    trigger: "item",
                    formatter: "{a} <br/>{b}: {c} ({d}%)",
                    position: function(p) {
                        //其中p为当前鼠标的位置
                        return [p[0] + 10, p[1] - 10];
                    }
                },
                legend: {
                    top: "90%",
                    itemWidth: 10,
                    itemHeight: 10,
                    selectedMode:false,//取消图例上的点击事件
                    data: ["A故障", "B故障", "C故障", "D故障", "E故障"],
                    textStyle: {
                        color: "rgba(255,255,255,.5)",
                        fontSize: "12"
                    }
                },
                grid: {
                        top: "16%",
                        left: "center",
                        right: "",
                        bottom: "0%",
                        show: true,//边框
                        borderColor: "#012f4a",
                        containLabel: true,//
                },
                series: [
                    {
                        name: "故障类型占比:",
                        type: "pie",
                        center: ["50%", "42%"],
                        radius: ["40%", "60%"],
                        color: [
                            "#065aab",
                            "#066eab",
                            "#0682ab",
                            "#0696ab",
                            "#06a0ab",
                            "#06b4ab",
                            "#06c8ab",
                            "#06dcab",
                            "#06f0ab"
                        ],
                        label: { show: false },
                        labelLine: { show: false },
                        data: [
                            { value: 1, name: "A故障" },
                            { value: 4, name: "B故障" },
                            { value: 2, name: "C故障" },
                            { value: 2, name: "D故障" },
                            { value: 1, name: "E故障" }
                        ]
                    }
                ]
            };
            // 使用刚指定的配置项和数据显示图表。
            myChart.setOption(option);
            window.addEventListener("resize", function() {
                myChart.resize();
            });
        }
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

        h2 {
            height: 0.4rem;
            line-height: 0.5rem;
            text-align: center;
            color: #fff;
            font-size: 0.25rem;
            font-weight: 400;
        }
    }
    #customized{
        height:2.6rem;
    }
</style>