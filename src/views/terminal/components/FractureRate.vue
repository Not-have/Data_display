<!-- 
 * @FileDescription:在线率折线图
 * @Author: 李勇
 * @Date: 2020-07-22    18：17
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div id="fracture" style="height:4rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.booklet();
        })
    },
    methods:{
        booklet(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('fracture'));
            // 指定图表的配置项和数据
            var option = {
                title: {
                    text: '折线图堆叠',
                    top:"5%",
                    left:"center",
                    textStyle: {
                        fontWeight: '400',
                        fontSize:19,
                        color:'#fff'//rgb(97, 142, 205)
                    },
                },
                tooltip: {
                    trigger: 'axis'
                },
                legend: {
                    data: ['视频广告'],
                    bottom:"0%",//图例位置
                    selectedMode:false,//取消图例上的点击事件
                    textStyle: { //图例文字的样式
                    	color:'#fff'
                    },
                },
                grid: {
                    top:"20%",
                    left: '3%',
                    right: '4%',
                    bottom: '8%',
                    containLabel: true
                },
                //他是图表的 下载属性
                toolbox: {
                    feature: {
                        saveAsImage: {}
                    }
                },
                xAxis: {
                    type: 'category',
                    boundaryGap: false,
                    data: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
                    axisLabel: {
                        fontSize:'12',
                        color:"#fff",
                        showMaxLabel: true, 
                        interval:0, //坐标刻度之间的显示间隔，默认就可以了（默认是不重叠）
                        rotate:20 ,  //调整数值改变倾斜的幅度（范围-90到90）
                        
                    },
                    //坐标轴刻度相关设置
                    axisTick: {
                        show: true,
                        alignWithLabel: true,//true 的时候有效，可以保证刻度线和标签对齐
                        lineStyle:{
                        	color:'white'// x轴刻度的颜色
                        }    
                    },
                    axisLine: {
                        // x轴是否显示
                        show:true,
                        //定义x轴颜色
                        lineStyle: {
                        	color: 'white'
                        }
                    },
                },
                yAxis: {
                    type: 'value',
                    splitLine: {
                    	show: false
                    },
                    axisLabel:{
                        color:"#fff",
                    },
                    axisTick: {
                        show: true,
                        alignWithLabel: true,//true 的时候有效，可以保证刻度线和标签对齐
                        lineStyle:{
                        	color:'white'// x轴刻度的颜色
                        }    
                    },
                    axisLine: {
                        // x轴是否显示
                        show:true,
                        //定义x轴颜色
                        lineStyle: {
                        	color: 'white'
                        }
                    },
                },
                series: [
                    {
                        name: '视频广告',
                        type: 'line',
                        stack: '总量',
                        data: [150, 232, 201, 154, 190, 330, 410],
                        markLine: {
                            silent: true,
                            lineStyle: {
                                color: 'red', // 这儿设置安全基线颜色
                                normal: {
                                    type:"solid",
                                    color: 'red',
                                }
                            },
                            data: [{
                                yAxis:200
                            }],
                        },
                        itemStyle : { 
                            normal : { 
                                color:'#275F82', //改变折线点的颜色
                                lineStyle:{ 
                                    color:'#60cda0' //改变折线颜色
                                } 
                            } 
                        },
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

</style>