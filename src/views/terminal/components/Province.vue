<!--
 * @Descripttion: (对该文件的信息描述)   echarts地图的省级流向图（即就是 省级地图）
 * @version: (版本)
 * @Author: (作者)  李勇
 * @Date: (文件创建时间)   2020-07-29   14：34
 * @LastEditors: (最后更新作者)
 * @LastEditTime: (最后更新时间)
--> 
<template>
    <div id="economizes">
        
    </div>
</template>
<script>
import echarts from "echarts";
import 'echarts/map/js/province/shanxi1.js';
export default {
    created(){
        this.$nextTick(()=>{
            this.province();
        })
    },
    methods:{
        province(){
            var myChart = echarts.init(document.getElementById('economizes'));
            // var geoCoordMap = {//省级要在这里  写出各个市的坐标
            //     '西安': [108.948024,34.263161],
            //     '铜川市': [108.979608,34.916582],
            //     '宝鸡市': [107.14487,34.369315],
            //     '咸阳市': [108.705117,34.333439],
            //     '渭南市': [109.502882,34.499381],
            //     '延安市': [109.49081,36.596537],
            //     '汉中市': [107.028621,33.077668],
            //     '榆林市': [109.741193,38.290162],
            //     '安康市': [109.029273,32.6903],
            //     '商洛市': [109.939776,33.868319],
            // };
            // var XAData = [
                
            // ];

            // var XNData = [
              
            // ];

            // var YCData = [
               
            // ];
            //这个是小飞机的图标，根据需求替换
            var planePath = '';
            //var planePath = 'arrow';
            // var convertData = function (data) {
            //     var res = [];
            //     for (var i = 0; i < data.length; i++) {
                    
            //         var dataItem = data[i];

            //         var fromCoord = geoCoordMap[dataItem[0].name];
            //         var toCoord = geoCoordMap[dataItem[1].name];
            //         if (fromCoord && toCoord) {
            //             res.push({
            //                 fromName: dataItem[0].name,
            //                 toName: dataItem[1].name,
            //                 coords: [fromCoord, toCoord],
            //                 value: dataItem[1].value
            //             });
            //         }
            //     }
            //     return res;
            // };

            // var color = ['#a6c84c', '#ffa022', '#46bee9'];//航线的颜色
            var series = [];
            // [['西安', XAData], ['渭南市', XNData], ['商洛市', YCData]].forEach(function (item, i) {  
            //     series.push({
            //         name: item[0] + ' Top3',
            //         type: 'lines',
            //         zlevel: 1,
            //         effect: {
            //             show: true,
            //             period: 6,
            //             trailLength: 0.7,
            //             color: 'red',   //arrow箭头的颜色
            //             symbolSize: 3
            //         },
            //         lineStyle: {
            //             normal: {
            //                 color: color[i],
            //                 width: 0,
            //                 curveness: 0.2
            //             }
            //         },
            //         data: convertData(item[1])
            //     },
            //     {
            //         name: item[0] + ' Top3',
            //         type: 'lines',
            //         zlevel: 2,
            //         symbol: ['none', 'arrow'],
            //         symbolSize: 10,
            //         effect: {
            //             show: true,
            //             period: 6,
            //             trailLength: 0,
            //             symbol: planePath,
            //             symbolSize:0 //这块设为0，自动就没有小飞机了
            //         },
            //         lineStyle: {
            //             normal: {
            //                 color: color[i],
            //                 width: 1,
            //                 opacity: 0.6,
            //                 curveness: 0.2
            //             }
            //         },
            //         data: convertData(item[1])
            //     },
            //     {
            //         name: item[0] + ' Top3',
            //         type: 'effectScatter',
            //         coordinateSystem: 'geo',
            //         zlevel: 2,
            //         rippleEffect: {
            //             brushType: 'stroke'
            //         },
            //         label: {
            //             normal: {
            //                 show: true,
            //                 position: 'right',
            //                 formatter: '{b}'
            //             }
            //         },
            //         symbolSize: function (val) {
            //             return val[2] / 8;
            //         },
            //         itemStyle: {
            //             normal: {
            //                 color: color[i],
            //             },
            //             emphasis: {
            //                 areaColor: '#2B91B7'
            //             }
            //         },
            //         data: item[1].map(function (dataItem) {
            //             return {
            //                 name: dataItem[1].name,
            //                 value: geoCoordMap[dataItem[1].name].concat([dataItem[1].value])
            //             };
            //         })
            //     });
            // });
            var option = {
                backgroundColor: '',
                title : {
                    text: '',
                    subtext: '',
                    left: 'center',
                    textStyle : {
                        color: '#fff'
                    }
                },
                // tooltip : {
                //     trigger: 'item', 
                //     formatter:function(params, ticket, callback){
                //         if(params.seriesType=="effectScatter") {
                //             return "线路："+params.data.name+""+params.data.value[2];
                //         }else if(params.seriesType=="lines"){
                //             return params.data.fromName+">"+params.data.toName+"<br />"+params.data.value;
                //         }else{
                //             return params.name;
                //         }
                //     } 
                // },
                // legend: {
                //     orient: 'vertical',
                //     top: 'bottom',
                //     left: 'right',
                //     data:['西安 Top3', '渭南市 Top3', '商洛市 Top3'],
                //     textStyle: {
                //         color: '#fff'
                //     },
                //     selectedMode: 'multiple'
                // },
                geo: {
                    map:"陕西",//这块是重点，在node_modules/echarts/map/js里面去看，你引入的那个，就去看那个的名字 registerMap后面 紧跟的 第一个 就是名字
                    label: {
                        // 显示市区的名字，直接显示，不用划过在显示
                        normal: {
                            show: false,
                            color:'rgba(255, 255, 255, 0.5)'
                        },
                        emphasis: {
                            show: true,
                            color:'#fff'
                        }
                    },
                    // 把中国地图放大了    倍
                    zoom:1.2,
                    roam: false,//这里设置是否允许，放大 我们的地图
                    itemStyle: {
                        normal: {
                            // 地图省份的背景颜色
                            areaColor: 'rgba(20, 41, 87,0.6)',
                            borderColor: 'rgba(43, 196, 243, 1)',
                            borderWidth: 1,
                        },
                        emphasis: {
                            areaColor: '#2B91B7'
                        }
                    }
                },
                series: series      
            };
            myChart.setOption(option);
            window.addEventListener("resize", function() {
                myChart.resize();
            });
        
        }
    }
}
</script>
<style lang="scss" scoped>
    #economizes{
        height:6.5rem;
    }
</style>