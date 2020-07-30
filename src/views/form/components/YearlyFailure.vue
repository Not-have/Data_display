<!-- 
 * @FileDescription: 年度故障区域，柱状图和饼状图
 * @Author: 李勇
 * @Date: 2020-07-20    11:10
 * @LastEditors: 李勇
 * @LastEditTime: 2020-07-28 11：20
 -->
<template>
    <div class="panel">
        <h2>2011全国宏观经济指标</h2>
        <div id="cylinder_circle" style="height:5.9rem">
            
        </div>
        <div class="panel-footer"></div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.cylinder();
        })
    },
    methods: {
        cylinder(){
            var myChart = echarts.init(document.getElementById('cylinder_circle'));
            var dataMap = {};
            function dataFormatter(obj) {
                // console.log(obj);
                var pList = ['北京','天津','河北','山西','内蒙古','辽宁','吉林','黑龙江'];
                var temp;
                for (var year = 2011; year <= 2011; year++) {
                    var max = 0;
                    var sum = 0;
                    temp = obj[year];
                    for (var i = 0, l = temp.length; i < l; i++) {
                        // console.log(temp);
                        max = Math.max(max, temp[i]);
                        sum += temp[i];
                        obj[year][i] = {
                            name: pList[i],
                            value: temp[i]
                        };
                    }
                    obj[year + 'max'] = Math.floor(max / 100) * 100;
                    obj[year + 'sum'] = sum;
                }
                return obj;
            }
            dataMap.dataGDP = dataFormatter({
                //max : 60000,
                2011:[16251.93,11307.28,24515.76,11237.55,14359.88,22226.7,10568.83,12582]
            });

            dataMap.dataPI = dataFormatter({
                //max : 4000,
                2011:[136.27,159.72,2905.73,641.42,1306.3,1915.57,1277.44,1701.5]
            });

            dataMap.dataSI = dataFormatter({
                //max : 26600,
                2011:[3752.48,5928.32,13126.86,6635.26,8037.69,12152.15,5611.48,5962.41]
            });

            dataMap.dataTI = dataFormatter({
                //max : 25000,
                2011:[5219.24,8483.17,3960.87,5015.89,8158.98,3679.91,4918.09,11142.86]
            });

            dataMap.dataEstate = dataFormatter({
                //max : 3600,
                2011:[1074.93,411.46,918.02,224.91,384.76,876.12,238.61,492.1]
            });

            dataMap.dataFinancial = dataFormatter({
                //max : 3200
                2011:[1074.93,411.46,918.02,224.91,384.76,876.12,238.61,492.1]
            });

            var option = {
                baseOption: {
                    timeline: {
                        show:false,
                        axisType: 'category',
                        realtime: false,
                        loop: false,
                        autoPlay: true,
                        data: [
                        ],
                        label: {
                            formatter : function(s) {
                                return (new Date(s)).getFullYear();
                            }
                        }
                    },
                    // title: {
                    //     text:'', 
                    //     left:"center",
                        
                    //     textStyle: {
                    //         color: "white",
                    //         fontSize:"16",
                    //         fontWeight :'normal'
                    //     }
                    // },
                    tooltip: {

                    },
                    legend: {
                        left: 'center',
                        bottom:10,
                        textStyle: { //图例文字的样式
                            color: '#fff'
                        },
                        data: ['第一产业', '第二产业', '第三产业', 'GDP', '金融', '房地产']
                    },
                    calculable : true,
                    grid: {
                        top: "80%",
                        bottom: "90%",
                        tooltip: {
                            trigger: 'axis',
                            axisPointer: {
                                type: 'shadow',
                                label: {
                                    show:false,
                                    formatter: function (params) {
                                        return params.value.replace('\n','');
                                    }
                                }
                            }
                        }
                    },
                    xAxis: [
                        {
                            'type':'category',
                            'data':[
                                '北京','\n天津','河北','\n山西','内蒙古','\n辽宁','吉林','\n黑龙江'
                            ],
                            axisLabel: {
                                color: "white",
                            }, 
                            axisTick:{
                                lineStyle:{
                                    color:'white'// x轴刻度的颜色
                                }    
                            },
                            axisLine: {
                                show: true,
                                lineStyle: {
                                    color: 'white'
                                }
                            },
                        }
                    ],
                    yAxis: [
                        {
                            type: 'value',
                            name: 'GDP（亿元）',
                            axisLabel: {
                                fontSize:'12',
                            },
                            axisLine: {
                                show: true,
                                lineStyle: {
                                    color: 'white'
                                }
                            },
                            splitLine: {
                                show: false,
                                lineStyle:{
                                    color:'white'// x轴坐标轴颜色
                                }  
                            },
                            axisTick:{
                                lineStyle:{
                                    color:'white'// x轴刻度的颜色
                                }    
                            },                        
                        }
                    ],
                    series: [
                        {name: 'GDP', type: 'bar'},
                        {name: '金融', type: 'bar'},
                        {name: '房地产', type: 'bar'},
                        {name: '第一产业', type: 'bar'},
                        {name: '第二产业', type: 'bar'},
                        {name: '第三产业', type: 'bar'},
                        {
                            name: 'GDP占比',
                            type: 'pie',
                            center: ['75%', '35%'],
                            radius: '20%',
                            z: 100
                        },
                    ]
                },
                options: [
                    {
                        series : [
                            {data: dataMap.dataGDP['2011']},
                            {data: dataMap.dataFinancial['2011']},
                            {data: dataMap.dataEstate['2011']},
                            {data: dataMap.dataPI['2011']},
                            {data: dataMap.dataSI['2011']},
                            {data: dataMap.dataTI['2011']},
                            {data: [
                                {name: '第一产业', value: dataMap.dataPI['2011sum']},
                                {name: '第二产业', value: dataMap.dataSI['2011sum']},
                                {name: '第三产业', value: dataMap.dataTI['2011sum']}
                            ]}
                        ]
                    }
                ]
            };
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