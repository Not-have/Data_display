<!-- 
 * @FileDescription:区域（县） 线路 top
 * @Author: 李勇
 * @Date: 2020-07-23    15:09
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div id="top" style="height:6.5rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.topClick();
        })
    },
    methods:{
        topClick(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('top'));
            var plantCap = [{
                name: '花',
                value: 'flower'
            }, {
                name: '特色餐厅',
                value: 'restaurant '
            }, {
                name: '八景',
                value: 'scenery '
            }, {
                name: '红嘴鸥',
                value: 'gull'
            }, {
                name: '酒吧',
                value: 'bar '
            }, {
                name: '歌舞表演',
                value: 'perform'
            }, {
                name: '商业街',
                value: 'street'
            }];

            var datalist = [{
                offset: [50, 50],
                symbolSize: 120,
                opacity: .95,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#29c0fb'
                }, {
                    offset: 1,
                    color: '#2dc5b9'
                }]),
            }, {
                offset: [38, 70],
                symbolSize: 95,
                opacity: .95,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#35d17e'
                }, {
                    offset: 1,
                    color: '#49ddb2'
                }]),
            }, {
                offset: [23, 43],
                symbolSize: 90,
                opacity: .95,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#e5d273'
                }, {
                    offset: 1,
                    color: '#e4a37f'
                }]),
            }, {
                offset: [68, 40],
                symbolSize: 90,
                opacity: .95,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#277aec'
                }, {
                    offset: 1,
                    color: '#57c5ec'
                }]),
            }, {
                offset: [38, 20],
                symbolSize: 65,
                opacity: .95,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#e54948'
                }, {
                    offset: 1,
                    color: '#f08456'
                }]),
            }, {
                offset: [56, 15],
                symbolSize: 68,
                opacity: .7,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#11c46e'
                }, {
                    offset: 1,
                    color: '#f08456'
                }]),
            }, {
                offset: [65, 75],
                symbolSize: 65,
                opacity: .68,
                color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
                    offset: 0,
                    color: '#ff4141'
                }, {
                    offset: 1,
                    color: '#ff8989'
                }]),
            }];
            var datas = [];
            for (var i = 0; i < plantCap.length; i++) {
                var item = plantCap[i];
                var itemToStyle = datalist[i];
                datas.push({
                    name: item.name + '\n' + item.value,
                    value: itemToStyle.offset,
                    symbolSize: itemToStyle.symbolSize,
                    label: {
                        normal: {
                            textStyle: {
                                fontSize: 13,
                                lineHeight: 17,
                            }
                        }
                    },
                    itemStyle: {
                        normal: {
                            color: itemToStyle.color,
                            opacity: itemToStyle.opacity
                        }
                    },
                })
            }
            var option = {
                backgroundColor:'',
                title: {
                    text: "",//标题内容
                    left:"center",//居中
                    textStyle: {
                        fontSize:19,//文字大小
                        color:"white",//文字颜色
                        fontWeight:'500'//文字粗细
                    }
                },
                grid: {
                    show: false,
                    top:"1%",
                    bottom:""
                },
                xAxis: [{
                    gridIndex: 0,
                    type: 'value',
                    show: false,
                    min: 0,
                    max: 100,
                    nameLocation: 'middle',
                    nameGap: 5
                }],
                yAxis: [{
                    gridIndex: 0,
                    min: 0,
                    show: false,
                    max: 100,
                    nameLocation: 'middle',
                    nameGap: 30
                }],
                series: [{
                    type: 'effectScatter',
                    // symbol: 'circle',
                    // symbolSize: 120,
                    symbolSize: function(val) {
                        return Math.max(val[2] / 100, 8);
                    },
                    showEffectOn: 'render',
                    rippleEffect: {
                        brushType: 'stroke'
                    },
                    hoverAnimation: true,
                    label: {
                        normal: {
                            show: true,
                            formatter: '{b}',
                            color: '#fff',
                            textStyle: {
                                fontSize: '20'
                            }
                        },
                    },
                    itemStyle: {
                        normal: {
                            color: '#00acea'
                        }
                    },
                    data: datas
                }, {
                    // name: 'pm2.5',
                    type: 'effectScatter',
                    data: datas,
                    symbolSize: function(val) {
                        return Math.max(val[2] / 200, 8);
                    },
                    label: {
                        normal: {
                            show: true,
                            formatter: '{b}',
                            color: '#fff',
                            textStyle: {
                                fontSize: '20'
                            }
                        },
                    },
                    itemStyle: {
                        normal: {
                            color: '#FF8C00',
                            position: 'right',
                            show: true
                        }
                    }
                }]
            };
            // 使用刚指定的配置项和数据显示图表。
            myChart.setOption(option);
            window.addEventListener("resize", function() {
                myChart.resize();
            });
        }
    }
}
</script>
<style lang="scss" scoped>

</style>