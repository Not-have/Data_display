<!-- 
 * @FileDescription:终端类型占比图
 * @Author: 李勇
 * @Date: 2020-07-17    11：20
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div class="panel">
        <p>终端类型占比</p>
        <div id="mold" style="height:2.6rem;"></div>
        <div class="panel-footer"></div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created() {
        this.$nextTick(()=>{
            this.moldClick();
        })
    },
    methods:{
        moldClick(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('mold'));
            // 指定图表的配置项和数据
            var option = {
                // 这个里面指定图标的样式和数据
                    legend: {
                        top: "86%",
                        itemWidth: 10,
                        itemHeight: 10,
                        selectedMode:false,//取消图例上的点击事件
                        textStyle: {
                            color: "rgba(255,255,255,.5)",
                            fontSize: "12"
                        }
                    },
                    tooltip: {
                        trigger: "item",
                        formatter: "{a} <br/>{b} : {c} ({d}%)"
                    },
                    // 注意颜色写的位置
                    color: [
                        "#006cff",
                        "#60cda0",
                        "#ed8884",
                        "#ff9f7f",
                        "#0096ff",
                        "#9fe6b8",
                        "#32c5e9",
                        "#1d9dff"
                    ],
                    series: [
                        {
                            name: "点位统计",
                            type: "pie",
                            // 如果radius是百分比则必须加引号
                            radius: ["10%", "70%"],
                            center: ["50%", "42%"],
                            roseType: "radius",
                            data: [
                                { value: 20, name: "云南" },
                                { value: 26, name: "北京" },
                                { value: 24, name: "山东" },
                                { value: 25, name: "河北" },
                                { value: 20, name: "江苏" },
                                { value: 25, name: "浙江" },
                                { value: 30, name: "深圳" },
                                { value: 42, name: "广东" }
                            ],
                            // 修饰饼形图文字相关的样式 label对象
                            label: {
                                fontSize: 10
                            },
                            // 修饰引导线样式
                            labelLine: {
                                // 连接到图形的线长度
                                length: 10,
                                // 连接到文字的线长度
                                length2: 10
                            }
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
        p{
            height: 0.6rem;
            line-height: 0.6rem;
            text-align: center;
            color: #fff;
            font-size: 0.25rem;
            font-weight: 400;
        }
    }
</style>