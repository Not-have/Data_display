<!-- 
 * @FileDescription:获取当前时间 ：区域终端折线图
 * @Author: 李勇
 * @Date: 2020-07-17    09：26
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div>
        <div class="panel">
            <h2>
                各区域终端数
            </h2>
            <div class="chart" id="terminal"></div>
            <div class="panel-footer"></div>
        </div>
    </div>
</template>
<script>
import echarts from "echarts"
export default {
    created() {
        this.$nextTick(()=>{
            this.terminClick();
        })
    },
    methods: {
        terminClick(){

            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('terminal'));
            var data = [70, 34, 60, 78, 69];
            var titlename = ["HTML5", "CSS3", "javascript", "VUE", "NODE"];
            var valdata = [702, 350, 610, 793, 664];
            var myColor = ["#1089E7", "#F57474", "#56D0E3", "#F8B448", "#8B78F6"];
            // 指定图表的配置项和数据
            var option = {
                // 这个里面指定图标的样式和数据
                grid: {
                    top: "3%",
                    left: "18%",
                    bottom: "2%"
                },
                xAxis: {
                    show: false
                },
                yAxis: [
                    {
                        show: true,
                        data: titlename,
                        inverse: true,
                        axisLine: {
                        show: false
                        },
                        splitLine: {
                        show: false
                        },
                        axisTick: {
                        show: false
                        },
                        axisLabel: {
                        color: "#fff",

                        rich: {
                            lg: {
                                backgroundColor: "#339911",
                                color: "#fff",
                                borderRadius: 15,
                                // padding: 5,
                                align: "center",
                                width: 15,
                                height: 15
                            }
                        }
                        }
                    },
                    {
                        show: true,
                        inverse: true,
                        data: valdata,
                        axisLabel: {
                        textStyle: {
                            fontSize: 12,
                            color: "#fff"
                        }
                        }
                    }
                ],
                series: [
                    {
                        name: "条",
                        type: "bar",
                        yAxisIndex:0,
                        data: data,
                        barCategoryGap:20,
                        barWidth: 10,
                        barGap:'10%',
                        itemStyle: {
                        normal: {
                            barBorderRadius: 20,
                            color: function(params) {
                                var num = myColor.length;
                                return myColor[params.dataIndex % num];
                            }
                        }
                        },
                        
                    },
                    {
                        name: "框",
                        type: "bar",
                        yAxisIndex: 1,
                        barCategoryGap: 50,
                        barGap:'30%',
                        data: [100, 100, 100, 100, 100],
                        barWidth: 15,
                        itemStyle: {
                        normal: {
                            color: "none",
                            borderColor: "#00c1de",
                            borderWidth:3,
                            barBorderRadius: 15
                        }
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

        h2 {
            height: 0.4rem;
            line-height: 0.5rem;
            text-align: center;
            color: #fff;
            font-size: 0.25rem;
            font-weight: 400;
        }
        .chart {
            height:2.6rem;
        }   
    }
</style>