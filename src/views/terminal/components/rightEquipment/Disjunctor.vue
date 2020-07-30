<template>
    <div id="disjunctor" style="height:3rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
import 'echarts-liquidfill';
export default {
    created(){
        this.$nextTick(()=>{
            this.junctor();
        })
    },
    methods:{
        junctor(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('disjunctor'));
            const data =  [0.68, 0.36]
            var option = {
                title: {
            	    text: "开关分合占比",//标题内容
                    left:"center",//居中
                    top:"4%",
                    textStyle: {
                        fontSize:19,//文字大小
                        color:"#fff",//文字颜色
                        fontWeight:'500'//文字粗细
                    }
                },
                // x轴
                xAxis:{
                    show:false, // 不显示
                },
                // y轴
                yAxis: {
                    show:false, // 不显示
                },
                grid:{
                    right:'40',
                    bottom:'0%',
                    left:0,
                    top:""
                }, 
                series: [{
                    type: 'liquidFill',
                    radius: '65%',  // 半径大小
                    center: ['50%', '50%'],    // 布局位置
                    data, // 水球波纹值
                    
                    outline: { // 轮廓设置
                        show: true,
                        borderDistance: 2, // 轮廓间距
                        itemStyle: {
                            borderColor: '#294D99', // 轮廓颜色
                            borderWidth: 4, // 轮廓大小
                            shadowBlur: 'none', // 轮廓阴影
                        }
                    },
                },{
                    type: 'line', // 折线图
                    markLine: {
                        silent: true, // 不触发鼠标事件
                        symbol:'', // 标线两端样式
                        lineStyle:{ // 标线样式
                            color: '#f00',
                            type: 'solid'
                        }, 
                        data: [{ // 标线数据
                            yAxis: data // y 轴
                        }]
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