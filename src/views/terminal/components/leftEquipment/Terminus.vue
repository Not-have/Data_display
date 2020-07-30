<template>
    <div id="terminus" style="height:3.4rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
export default {
    created(){
        this.$nextTick(()=>{
            this.trigger();
        })
    },
    methods:{
        trigger(){
            // 基于准备好的dom，初始化echarts实例
            var myChart = echarts.init(document.getElementById('terminus'));
            // 指定图表的配置项和数据
            var option = {
                title: {
                    text: "",//标题内容
                    left:"center",//居中
                    textStyle: {
                        fontSize:0,//文字大小
                        color:"",//文字颜色
                        fontWeight:'500'//文字粗细
                    }
                },
                // 注意颜色写的位置
                color: [
                    "#006cff",
                    "#60cda0",
                    "#ed8884",
                    "#9fe6b8",
                    "#32c5e9",
                    "#1d9dff"
                ],
                series: [{
                    type: 'pie',
                    radius: '75%',
                    center: ['50%', '50%'],
                    roseType: 'radius',
                    labelLine: {
                        show: true,
                        length: 15,
                        length2: 110
                    },
                    label: {
                        formatter: '{b|{b} {d}%}\n{c|●}',
                        rich: {
                            c: {//小圆点
                                padding: [0, -10, 0, -10]
                            },
                            b: {
                                padding: [0, -110, -15, -110],
                                color: '#8ebef2',
                                fontSize: 14
                            }
                        }
                    },
                    data: [{
                            value: 100,
                            name: '乒乓球',
                        },
                        {
                            value: 120,
                            name: '羽毛球'
                        },
                        {
                            value: 100,
                            name: '篮球'
                        },
                        {
                            value: 140,
                            name: '足球'
                        }
                    ]
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