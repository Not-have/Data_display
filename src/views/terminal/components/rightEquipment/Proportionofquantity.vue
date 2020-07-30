<template>
    <div id="quantity" style="height:3.4rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.proportion();
        })
    },
    methods:{
        proportion(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('quantity'));
            var option = {
                title: {
            	    text: "地区（县）top5占比-数量",//标题内容
            	    left:"center",//居中
                    textStyle: {
                        fontSize:19,//文字大小
                        color:"#fff",//文字颜色
                        fontWeight:'400'//文字粗细
                    }
                },
                grid: {
                    left: '6%',
                    right: '5%',
                    bottom: '0%',
                    top: '10%',
                    containLabel: true
                },
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'none'
                    },
                    formatter: function(params) {
                        return params[0].name + '<br/>' +
                            "<span style='display:inline-block;margin-right:5px;border-radius:10px;width:9px;height:9px;background-color:rgba(36,207,233,0.9)'></span>" +
                            params[0].seriesName + ' : ' + Number((params[0].value)).toLocaleString() + ' 元<br/>'
                    }
                },
                backgroundColor: '',
                xAxis: {
                    show: false,
                    type: 'value'
                },
                yAxis: [{
                    type: 'category',
                    inverse: true,
                    axisLabel: {
                        show: true,
                        textStyle: {
                            color: '#fff'
                        },
                    },
                    splitLine: {
                        show: false
                    },
                    axisTick: {
                        show: false
                    },
                    axisLine: {
                        show: false
                    },
                    data: ['大米', '玉米', '蔬菜', '鸡蛋', '坚果']
                }, {
                    type: 'category',
                    inverse: true,
                    axisTick: 'none',
                    axisLine: 'none',
                    show: true,
                    axisLabel: {
                        textStyle: {
                            color: '#ffffff',
                            fontSize: '12'
                        },
                        formatter: function(value) {
                            if (value >= 10000) {
                                return value.toLocaleString() + '';
                            } else {
                                return value.toLocaleString();
                            }
                        },
                    },
                    data: [200, 220, 1000, 500,10]//这个是左侧显示的数字
                }],
                series: [{
                        name: '金额',
                        type: 'bar',
                        zlevel: 1,
                        itemStyle: {
                            normal: {
                                barBorderRadius: 30,
                                color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
                                    offset: 0,
                                    color: 'rgb(57,89,255,1)'
                                }, {
                                    offset: 1,
                                    color: 'rgb(46,200,207,1)'
                                }]),
                            },
                        },
                        barWidth: 20,
                        data: [200, 220, 1000, 500,10]//这个是数量
                    },
                    {
                        name: '背景',
                        type: 'bar',
                        barWidth: 20,
                        barGap: '-100%',
                        data: [5000, 5000, 5000, 5000, 5000],//这个是背景的长度（这个长度，设置成，最大数量×10），个数也要和上面一样
                        itemStyle: {
                            normal: {
                                color: 'rgba(24,31,68,1)',
                                barBorderRadius: 30,
                            }
                        },
                    },
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

</style>