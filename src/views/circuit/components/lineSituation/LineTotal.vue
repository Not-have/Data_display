<template>
    <div id="total">
        <!-- 线路总数 -->
        
    </div>
</template>
<script>
import echarts from "echarts";
import 'echarts-liquidfill';
export default {
    created(){
        this.$nextTick(()=>{
            this.totalClick();
        })
    },
    methods:{
        totalClick(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('total'));
            var option = {
                title: {
                    text: '',
                    left: 'center',
                    top:"1%",
                    textStyle: {
                        color: '#333',
                        fontWeight: 'bold',
                        fontSize: 20
                    }
                },
                series: [{
                    name: '水球图',
                    type: 'liquidFill',
                    radius: '65%',
                    center: ['50%', '55%'],
                    waveAnimation: 10, // 动画时长
                    amplitude: 40, // 振幅
                    data: [0.6],
                    color: 'rgba(68, 197, 253,1)',
                    label: {
                        normal: {
                            color: '#44C5FD',
                            textStyle: {
                                fontSize: 18,
                                fontWeight: 'bold'
                            }
                        }
                    },
                    outline: {
                        show: true,
                        borderDistance: 5,
                        itemStyle: {
                            borderColor: 'rgba(68, 197, 253,1)',
                            borderWidth: 2
                        }
                    },
                    backgroundStyle: {
                        color: 'rgba(68, 197, 253,.3)'
                    }
                }]
            }
            myChart.setOption(option);
            window.addEventListener("resize", function() {
                myChart.resize();
            });
        }
    }
}
</script>
<style lang="scss" scoped>
    #total{
        height:3rem;
        width:50%;
    }
</style>