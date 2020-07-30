<!-- 
 * @FileDescription:月线路故障
 * @Author: 李勇
 * @Date: 2020-07-20    15：42
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div>
        <div class="panel">
            <h2>月故障线路</h2>
            <div id="monthly" style="height:3.6rem"></div>
            <div class="panel-footer"></div>
        </div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.Mhitch();
        })
    },
    methods: {
        Mhitch(){
            var myChart = echarts.init(document.getElementById('monthly'));
            const CubeLeft = echarts.graphic.extendShape({
                shape: {
                    x: 0,
                    y: 0
                },
                buildPath: function(ctx, shape) {
                    const xAxisPoint = shape.xAxisPoint
                    const c0 = [shape.x, shape.y]
                    const c1 = [shape.x - 9, shape.y - 9]
                    const c2 = [xAxisPoint[0] - 9, xAxisPoint[1] - 9]
                    const c3 = [xAxisPoint[0], xAxisPoint[1]]
                    ctx.moveTo(c0[0], c0[1]).lineTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).closePath()
                }
            })
            const CubeRight = echarts.graphic.extendShape({
                shape: {
                    x: 0,
                    y: 0
                },
                buildPath: function(ctx, shape) {
                    const xAxisPoint = shape.xAxisPoint
                    const c1 = [shape.x, shape.y]
                    const c2 = [xAxisPoint[0], xAxisPoint[1]]
                    const c3 = [xAxisPoint[0] + 18, xAxisPoint[1] - 9]
                    const c4 = [shape.x + 18, shape.y - 9]
                    ctx.moveTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).lineTo(c4[0], c4[1]).closePath()
                }
            })
            const CubeTop = echarts.graphic.extendShape({
                shape: {
                    x: 0,
                    y: 0
                },
                buildPath: function(ctx, shape) {
                    const c1 = [shape.x, shape.y]
                    const c2 = [shape.x + 18, shape.y - 9]
                    const c3 = [shape.x + 9, shape.y - 18]
                    const c4 = [shape.x - 9, shape.y - 9]
                    ctx.moveTo(c1[0], c1[1]).lineTo(c2[0], c2[1]).lineTo(c3[0], c3[1]).lineTo(c4[0], c4[1]).closePath()
                }
            })
            echarts.graphic.registerShape('CubeLeft', CubeLeft)
            echarts.graphic.registerShape('CubeRight', CubeRight)
            echarts.graphic.registerShape('CubeTop', CubeTop)
            const VALUE = [2012, 1230, 3790, 2349, 1654, 1230, 3790, 2349, 1654, 3790, 2349, 1654]
            var option = {
                backgroundColor:"",
                // title: {
                //     text: '月故障线路',
                //     top:"5%",
                //     left:"center",
                //     textStyle: {
                //         color: "white",
                //         fontSize:16,
                //         fontWeight :'normal'
                //     }
                // },
                tooltip: {
                    //提示框组件
                    trigger: "axis",
                    formatter: "{b}:{c0}", //提示框浮层内容格式器
                    axisPointer: { //坐标轴指示器
                        type: "shadow", //'shadow' 阴影指示器
                        label: {
                        backgroundColor: "#6a7985"
                        }
                    },
                    textStyle: {
                        color: "#fff",
                        fontStyle: "normal",
                        fontFamily: "微软雅黑",
                        fontSize: 12
                    },
                },
                grid: {
                    left:"1%",
                    right:"2%",
                    bottom: '6%',
                    top:"6%",
                    containLabel: true
                },
                xAxis: {
                    type: 'category',
                    data: ['德州', '德城区', '陵城区', '禹城市', '乐陵市', '临邑县',
                        '平原县', '夏津县', '武城县', '庆云县', '宁津县', '齐河县'
                    ],
                    axisLine: {
                        show: true,
                        lineStyle: {
                            color: 'white'
                        }
                    },
                    offset: 20,
                    axisTick: {
                        show: false,
                        length: 9,
                        alignWithLabel: true,
                        lineStyle: {
                            color: '#7DFFFD'
                        }
                    },
                    axisLabel: {
                        formatter: '{value}',
                        textStyle: { //改变刻度字体样式
                            color: '#fff',
                            fontSize:'10'
                        },
                        margin:-6 //
                    }
                },
                yAxis: {
                    type: 'value',
                    axisLine: {
                        show: true,
                        lineStyle: {
                            color:'white'
                        }
                    },
                    splitLine: {
                        show: false
                    },
                    axisTick: {
                        show: false
                    },
                    axisLabel: {
                        fontSize:14
                    },
                    boundaryGap: ['20%', '20%']
                },
                series: [{
                    type: 'custom',
                    renderItem: (params, api) => {
                        const location = api.coord([api.value(0), api.value(1)])
                        return {
                            type: 'group',
                            children: [{
                                type: 'CubeLeft',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0])
                                },
                                style: {
                                    fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                                            offset: 0,
                                            color: '#3B80E2'
                                        },
                                        {
                                            offset: 1,
                                            color: '#49BEE5'
                                        }
                                    ])
                                }
                            }, {
                                type: 'CubeRight',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0])
                                },
                                style: {
                                    fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                                            offset: 0,
                                            color: '#3B80E2'
                                        },
                                        {
                                            offset: 1,
                                            color: '#49BEE5'
                                        }
                                    ])
                                }
                            }, {
                                type: 'CubeTop',
                                shape: {
                                    api,
                                    xValue: api.value(0),
                                    yValue: api.value(1),
                                    x: location[0],
                                    y: location[1],
                                    xAxisPoint: api.coord([api.value(0), 0])
                                },
                                style: {
                                    fill: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                                            offset: 0,
                                            color: '#3B80E2'
                                        },
                                        {
                                            offset: 1,
                                            color: '#49BEE5'
                                        }
                                    ])
                                }
                            }]
                        }
                    },
                    data: VALUE
                }, {
                    type: 'bar',
                    label: {
                        normal: {
                            show:true,
                            position: 'top',
                            fontSize:12,
                            color: '#fff',
                            offset: [4, -25]
                        }
                    },
                    itemStyle: {
                        color: 'transparent'
                    },
                    data: VALUE
                }]
            }
            myChart.setOption(option);
            window.addEventListener("resize", function() {
                myChart.resize();
            });
        }
    },
}
</script>
<style lang="scss" scoped>
    @import "@/styles/item.scss";
</style>