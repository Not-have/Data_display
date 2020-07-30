<!-- 
 * @FileDescription:获取当前时间 ：今日新增故障的圆型图
 * @Author: 李勇
 * @Date: 2020-07-16    15：18
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div class="panel">
        <h2>今日新增故障</h2>
        <div id="quantity">
            
        </div>
        <div class="panel-footer"></div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    data() {
        return {
            num:0
        }
    },
    mounted() {
        

    },
    created() {
        this.$nextTick(()=>{
            this.jishi();
        })
    },
    methods: {
        jishi(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('quantity'));
            let angle = 0;//角度，用来做简单的动画效果的
            var value = 100;
            // 指定图表的配置项和数据
            var option = {
                // 这个里面指定图标的样式和数据
                backgroundColor:"",
                title: {
                        text: '{a|'+ this.num +'}{c|个}',
                        x: 'center',
                        y: 'center',
                        textStyle: {
                            rich:{
                                a: {
                                    fontSize:24,
                                    color: '#29EEF3'
                                },
                                
                                c: {
                                    fontSize: 22,
                                    color: '#29EEF3',
                                    // padding: [5,0]
                                }
                            }
                        }
                    },
                    grid: {
                        top: "16%",
                        left: "center",
                        bottom: "0%",
                    },
                    legend: {
                        type: "plain",
                        orient: "vertical",
                        align: "auto",
                        data: [{
                            name: '',
                            icon: "circle"
                        }, {
                            name: '',
                            icon: "circle"
                        }, {
                            name: '',
                            icon: "circle"
                        }, {
                            name: '',
                            icon: "circle"
                        }],
                        textStyle: {
                            color: "white",
                            fontSize: 16,
                            padding: [10, 1, 10, 0]
                        },
                        selectedMode:false
                    },
                    series: [ {
                            name: "ring5",
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                return {
                                    type: 'arc',
                                    shape: {
                                        cx: api.getWidth() / 2,
                                        cy: api.getHeight() / 2,
                                        r: Math.min(api.getWidth(), api.getHeight()) / 2 * 0.6,
                                        startAngle: (0+angle) * Math.PI / 180,
                                        endAngle: (90+angle) * Math.PI / 180
                                    },
                                    style: {
                                        stroke: "#0CD3DB",
                                        fill: "transparent",
                                        lineWidth: 1.5
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: "ring5",
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                return {
                                    type: 'arc',
                                    shape: {
                                        cx: api.getWidth() / 2,
                                        cy: api.getHeight() / 2,
                                        r: Math.min(api.getWidth(), api.getHeight()) / 2 * 0.6,
                                        startAngle: (180+angle) * Math.PI / 180,
                                        endAngle: (270+angle) * Math.PI / 180
                                    },
                                    style: {
                                        stroke: "#0CD3DB",
                                        fill: "transparent",
                                        lineWidth: 1.5
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: "ring5",
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                return {
                                    type: 'arc',
                                    shape: {
                                        cx: api.getWidth() / 2,
                                        cy: api.getHeight() / 2,
                                        r: Math.min(api.getWidth(), api.getHeight()) / 2 * 0.65,
                                        startAngle: (270+-angle) * Math.PI / 180,
                                        endAngle: (40+-angle) * Math.PI / 180
                                    },
                                    style: {
                                        stroke: "#0CD3DB",
                                        fill: "transparent",
                                        lineWidth: 1.5
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: "ring5",
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                return {
                                    type: 'arc',
                                    shape: {
                                        cx: api.getWidth() / 2,
                                        cy: api.getHeight() / 2,
                                        r: Math.min(api.getWidth(), api.getHeight()) / 2 * 0.65,
                                        startAngle: (90+-angle) * Math.PI / 180,
                                        endAngle: (220+-angle) * Math.PI / 180
                                    },
                                    style: {
                                        stroke: "#0CD3DB",
                                        fill: "transparent",
                                        lineWidth: 1.5
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: "ring5",
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                let x0 = api.getWidth() / 2;
                                let y0 = api.getHeight() / 2;
                                let r = Math.min(api.getWidth(), api.getHeight()) / 2 * 0.65;
                                let point = getCirlPoint(x0, y0, r, (90+-angle))
                                return {
                                    type: 'circle',
                                    shape: {
                                        cx: point.x,
                                        cy: point.y,
                                        r: 4
                                    },
                                    style: {
                                        stroke: "#0CD3DB",//粉
                                        fill: "#0CD3DB"
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: "ring5",  //绿点
                            type: 'custom',
                            coordinateSystem: "none",
                            renderItem: function(params, api) {
                                let x0 = api.getWidth() / 2;
                                let y0 = api.getHeight() / 2;
                                let r = Math.min(api.getWidth(), api.getHeight()) / 2 * 0.65;
                                let point = getCirlPoint(x0, y0, r, (270+-angle))
                                return {
                                    type: 'circle',
                                    shape: {
                                        cx: point.x,
                                        cy: point.y,
                                        r: 4
                                    },
                                    style: {
                                        stroke: "#0CD3DB",   //绿
                                        fill: "#0CD3DB"
                                    },
                                    silent: true
                                };
                            },
                            data: [0]
                        }, {
                            name: '',
                            type: 'pie',
                            radius: ['58%', '45%'],
                            silent: true,
                            clockwise: true,
                            startAngle: 90,
                            z: 0,
                            zlevel: 0,
                            label: {
                                normal: {
                                    position: "center",

                                }
                            },
                            data: [{
                                    value: value,
                                    name: "",
                                    itemStyle: {
                                        normal: {
                                            color: { // 完成的圆环的颜色
                                                colorStops: [{
                                                    offset: 0,
                                                    color: '#4FADFD' // 0% 处的颜色
                                                }, {
                                                    offset: 1,
                                                    color: '#4FADFD' // 100% 处的颜色
                                                }]
                                            },
                                        }
                                    }
                                },
                                {
                                    value: 100-value,
                                    name: "",
                                    label: {
                                        normal: {
                                            show: false
                                        }
                                    },
                                    itemStyle: {
                                        normal: {
                                            color: "#173164"
                                        }
                                    }
                                }
                            ]
                        },{
                            name: "",
                            type: "gauge",
                            radius: "58%",
                            center: ['50%', '50%'],
                            startAngle: 0,
                            endAngle: 359.9,
                            splitNumber: 8,
                            hoverAnimation: true,
                            axisTick: {
                                show: false
                            },
                            splitLine: {
                                length: 60,
                                lineStyle: {
                                    width: 5,
                                    color: "#061740"
                                }
                            },
                            axisLabel: {
                                show: false
                            },
                            pointer: {
                                show: false
                            },
                            axisLine: {
                                lineStyle: {
                                    opacity: 0
                                }
                            },
                            detail: {
                                show: false
                            },
                            data: [{
                                value: 0,
                                name: ""
                            }]
                        },
                        
                    ]

            };
            
            //获取圆上面某点的坐标(x0,y0表示坐标，r半径，angle角度)
            function getCirlPoint(x0, y0, r, angle) {
                let x1 = x0 + r * Math.cos(angle * Math.PI / 180)
                let y1 = y0 + r * Math.sin(angle * Math.PI / 180)
                return {
                    x: x1,
                    y: y1
                }  
            }
            function draw(){
                angle = angle+3
                myChart.setOption(option, true)
                window.addEventListener("resize", function() {
                    myChart.resize();
                });
            }
            
            setInterval(function() {
                draw()
            }, 100);
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
    #quantity{
        height:2.9rem;
        width:100%;  
        ::v-deep div{
            margin:0 !important;
            width:100% !important;
        }
    }

</style>