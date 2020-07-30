<!-- 
 * @FileDescription:终端页面
 * @Author: 李勇
 * @Date: 2020-07-21    14：21
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div id="wander">
        
    </div>
</template>
<script>
import echarts from "echarts";
import 'echarts/extension/bmap/bmap';
export default {
    created(){
        this.$nextTick(()=>{
            this.wanMap();
        })
    },
    methods:{
        wanMap(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('wander'));
            
            var data = [
                {name: '海门', value: 9},
                {name: '鄂尔多斯', value: 12},
                {name: '招远', value: 12},
                {name: '舟山', value: 12},
                {name: '齐齐哈尔', value: 14},
                {name: '盐城', value: 15},
                {name: '赤峰', value: 16},
                {name: '青岛', value: 18}
            ];

            var geoCoordMap = {
                '海门':[121.15,31.89],
                '鄂尔多斯':[109.781327,39.608266],
                '招远':[120.38,37.35],
                '舟山':[122.207216,29.985295],
                '齐齐哈尔':[123.97,47.33],
                '盐城':[120.13,33.38],
                '赤峰':[118.87,42.28],
                '青岛':[120.33,36.07],
            };

            var convertData = function (data) {
                var res = [];
                for (var i = 0; i < data.length; i++) {
                    var geoCoord = geoCoordMap[data[i].name];
                    if (geoCoord) {
                        res.push({
                            name: data[i].name,
                            value: geoCoord.concat(data[i].value)
                        });
                    }
                }
                return res;
            };
           
            var option = {
                backgroundColor: 'transparent',
                title: {
                    text: '流向图',
                    left: 'center',
                    textStyle: {
                        color: '#000',
                        fontSize:19,
                        fontWeight:'500'//文字粗细         
                    }
                },
                tooltip : {
                    trigger: 'item'
                },
                bmap: {
                    center: [104.114129, 37.550339],
                    zoom: 5,
                    roam: true,
                    mapStyle: {
                        styleJson: [
                            
                        ]
                    }
                },
                series : [
                    {
                        name: 'pm2.5',
                        type: 'scatter',
                        coordinateSystem: 'bmap',
                        data: convertData(data),
                        encode: {
                            value: 2
                        },
                        symbolSize: function (val) {
                            return val[2] / 10;
                        },
                        label: {
                            formatter: '{b}',
                            position: 'right'
                        },
                        itemStyle: {
                            color: '#ddb926'
                        },
                        emphasis: {
                            label: {
                                show: true
                            }
                        }
                    },
                    {
                        name: 'Top 5',
                        type: 'effectScatter',
                        coordinateSystem: 'bmap',
                        data: convertData(data.sort(function (a, b) {
                            return b.value - a.value;
                        }).slice(0, 6)),
                        encode: {
                            value: 2
                        },
                        symbolSize: function (val) {
                            return val[2] / 10;
                        },
                        showEffectOn: 'emphasis',
                        rippleEffect: {
                            brushType: 'stroke'
                        },
                        hoverAnimation: true,
                        label: {
                            formatter: '{b}',
                            position: 'right',
                            show: true
                        },
                        itemStyle: {
                            color: 'red',
                            shadowBlur: 10,
                            shadowColor: '#333'
                        },
                        zlevel: 1
                    },
                    {
                        type: 'custom',
                        coordinateSystem: 'bmap',
                        itemStyle: {
                            opacity: 0.5
                        },
                        animation: false,
                        silent: true,
                        data: [0],
                        z: -10
                    }
                ]

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
    #wander{
        height:6.5rem;
        width:100%;
        border-radius:10%;
        ::v-deep .BMap_cpyCtrl a{
           display: none;
        }
        ::v-deep .anchorBL img{
            display: none;
        }
        ::v-deep .BMap_cpyCtrl{
            display: none;
        }
    }
</style>