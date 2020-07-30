<template>
    <div id="dumolished" style="height:3rem;">

    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.lisged();
        })
    },
    methods:{
        lisged(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('dumolished'));
            // 指定图表的配置项和数据
            var option = {
                // 这个里面指定图标的样式和数据
                title:{
                    text:'终端数量',
                    left:"center",
                    top:"4%",
                    textStyle: {
            		    fontSize:19,//文字大小
            		    color:"#fff",//文字颜色
            		    fontWeight:'500'//文字粗细
            	    }
                },
                tooltip: {
                },
                series: [{
                    name: '',
                    type: 'pie',
                    radius: ['55%', '50%'],
                    center:['20%','50%'],
                    color:'#2f808f',
                    hoverAnimation:false,
                    label: {
                        normal: {
                            position: 'center'
                        }
                    },
                    data: [{
                        value: 72,
                        name: '我的仪表盘',
                        label: {
                            normal: {
                                formatter: '{c}\n\n我的仪表盘',
                                textStyle: {
                                    color: '#fff',
                                    fontSize: 14
                                }
                            }
                        },
                        itemStyle: {
                            normal: {
                                color: '#d8e8f2'
                            },
                            emphasis: {
                                color: '#d8e8f2'
                            }
                        },
                    }]
                },{
                    name: '',
                    type: 'pie',
                    radius: ['55%', '50%'],
                    center:['50%','50%'],
                    color:'#2f808f',
                    hoverAnimation:false,
                    label: {
                        normal: {
                            position: 'center'
                        }
                    },
                    data: [{
                        value: 50,
                        name: '我的图表',
                        label: {
                            normal: {
                                formatter: '{c}\n\n我的图表',
                                textStyle: {
                                    color: '#fff',
                                    fontSize: 14
                                }
                            }
                        },
                        itemStyle: {
                            normal: {
                                color: '#d8e8f2'
                            },
                            emphasis: {
                                color: '#d8e8f2'
                            }
                        },
                    }]
                },{
                    name: '',
                    type: 'pie',
                    radius: ['55%', '50%'],
                    center:['80%','50%'],
                    color:'#2f808f',
                    hoverAnimation:false,
                    label: {
                        normal: {
                            position: 'center'
                        }
                    },
                    data: [{
                        value: 86,
                        name: '我的数据集',
                        label: {
                            normal: {
                                formatter: '{c}\n\n我的数据集',
                                textStyle: {
                                    color: '#fff',
                                    fontSize: 14
                                }
                            }
                        },
                        itemStyle: {
                            normal: {
                                color: '#d8e8f2'
                            },
                            emphasis: {
                                color: '#d8e8f2'
                            }
                        },
                    }]
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
    #dumolished{
        box-sizing: border-box;
        padding:0 10%;
    }
</style>