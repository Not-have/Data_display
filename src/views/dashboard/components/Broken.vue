<!-- 
 * @FileDescription:本月区域故障折线图
 * @Author: 李勇
 * @Date: 2020-07-16    15：44
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div  class="panel">
        <h2>本月故障</h2>
        <div id="broken">
        </div>
        <div class="panel-footer"></div>
    </div>

</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.brokens();
        })
    },
    methods: {
        brokens(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('broken'));
            var data = {
                year: [
                    [24, 40, 101, 134, 90, 230, 210, 213, 120, 230, 210, 120],
                    [40, 40, 191, 324, 290, 330, 310, 213, 180, 200, 180, 79]
                ]
            };
            // 指定图表的配置项和数据
            var option = {
                tooltip: {
                // 通过坐标轴来触发
                    trigger: "axis"
                },
                legend: {
                    // 距离容器10%
                    left: "5%",
                    top:"1%",
                    // 修饰图例文字的颜色
                    textStyle: {
                        color: "#4c9bfd"
                    }
                    // 如果series 里面设置了name，此时图例组件的data可以省略
                    // data: ["邮件营销", "联盟广告"]
                },
                grid: {
                    top: "16%",
                    left: "1%",
                    right: "0.8%",
                    bottom: "0%",
                    show: true,
                    borderColor: "#012f4a",
                    containLabel: true
                },

                xAxis: {
                    type: "category",
                    boundaryGap: false,
                    data: [
                        "1月",
                        "2月",
                        "3月",
                        "4月",
                        "5月",
                        "6月",
                        "7月",
                        "8月",
                        "9月",
                        "10月",
                        "11月",
                        "12月"
                    ],
                    // 去除刻度
                    axisTick: {
                        show: false
                    },
                    // 修饰刻度标签的颜色
                    axisLabel: {
                        color: "rgba(255,255,255,.7)"
                    },
                    // 去除x坐标轴的颜色
                    axisLine: {
                        show: false
                    }
                },
                yAxis: {
                    type: "value",
                    // 去除刻度
                    axisTick: {
                        show: false
                    },
                    // 修饰刻度标签的颜色
                    axisLabel: {
                        color: "rgba(255,255,255,.7)"
                    },
                    // 修改y轴分割线的颜色
                    splitLine: {
                        lineStyle: {
                        color: "#012f4a"
                        }
                    }
                },
                series: [
                    {
                        name: "新增粉丝",
                        type: "line",
                        // 是否让线条圆滑显示
                        smooth: true,
                        data: data.year[0]
                    },
                    {
                        name: "新增游客",
                        type: "line",
                        smooth: true,
                        data: data.year[1]
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
    }
    #broken{
        height:2.6rem;
    }
</style>