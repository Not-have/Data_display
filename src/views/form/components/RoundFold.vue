<!-- 
 * @FileDescription: 当年月故障详情（折线图和饼状图联动）
 * @Author: 李勇
 * @Date: 2020-07-20    11:26
 * @LastEditors: 
 * @LastEditTime: 
 -->
<template>
    <div class="panel">
        <div id="round" style="height:6.3rem">
            
        </div>
        <div class="panel-footer"></div>
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.roundF();
        })
    },
    methods:{
        roundF(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('round'));
            // 指定图表的配置项和数据
            var option = {
                // 这个里面指定图标的样式和数据
                title: {
                    text:"月故障",//标题内容
                    left:"center",//居中
                    textStyle: {
                        fontSize:19,//文字大小
                        color:"white",//文字颜色
                        fontWeight:'400'//文字粗细
                    }
                },
                legend: {
                    bottom:0,//图例位置
                    selectedMode:false,//取消图例上的点击事件
                    textStyle: { //图例文字的样式
                        color: '#fff'
                    },
                },
                tooltip: {
                    trigger: 'axis',
                    showContent: false
                },
                dataset: {
                    source: [
                        ['product', '2012', '2013', '2014', '2015', '2016', '2017'],
                        ['Matcha Latte', 41.1, 30.4, 65.1, 53.3, 83.8, 98.7],
                        ['Milk Tea', 86.5, 92.1, 85.7, 83.1, 73.4, 55.1],
                        ['Cheese Cocoa', 24.1, 67.2, 79.5, 86.4, 65.2, 82.5],
                        ['Walnut Brownie', 55.2, 67.1, 69.2, 72.4, 53.9, 39.1]
                    ]
                },
                xAxis: {
                    type: 'category',
                    axisLine: {
                        // x轴是否显示
                        show: true,
                        //定义x轴颜色
                        lineStyle: {
                        	color: 'white'
                        }
                    },
                    
                },
                yAxis: {
                    gridIndex: 0,splitLine: {show: false},
                    axisLine: {
                        // x轴是否显示
                        show: true,
                        //定义x轴颜色
                        lineStyle: {
                        	color: 'white'
                        }
                    },
                },
                grid: {
                    top: '50%',
                },
                series: [
                    {type: 'line', smooth: true, seriesLayoutBy: 'row'},
                    {type: 'line', smooth: true, seriesLayoutBy: 'row'},
                    {type: 'line', smooth: true, seriesLayoutBy: 'row'},
                    {type: 'line', smooth: true, seriesLayoutBy: 'row'},
                    {
                        type: 'pie',
                        id: 'pie',
                        radius: '30%',
                        center: ['50%', '25%'],
                        label: {
                            formatter: '{b}: {@2012} ({d}%)'
                        },
                        encode: {
                            itemName: 'product',
                            value: '2012',
                            tooltip: '2012'
                        }
                    }
                ]
            };
            myChart.on('updateAxisPointer', function (event) {
                var xAxisInfo = event.axesInfo[0];
                if (xAxisInfo) {
                    var dimension = xAxisInfo.value + 1;
                    myChart.setOption({
                        series: {
                            id: 'pie',
                            label: {
                                formatter: '{b}: {@[' + dimension + ']} ({d}%)'
                            },
                            encode: {
                                value: dimension,
                                tooltip: dimension
                            }
                        }
                    });
                }
            });
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
    @import "@/styles/item.scss";
</style>