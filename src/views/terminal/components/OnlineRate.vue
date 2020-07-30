<!-- 
 * @FileDescription:在线率
 * @Author: 李勇
 * @Date: 2020-07-22    18：17
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div id="online" style="height:4rem">
        
    </div>
</template>
<script>
import echarts from "echarts";
import 'echarts-liquidfill';
export default {
    created(){
        this.$nextTick(()=>{
            this.onlineClick();
        })
    },
    methods:{
        onlineClick(){
            var myChart = echarts.init(document.getElementById('online'));
            var value = 0.12
            var data = [];
            data.push(value);
            data.push(value);
            data.push(value);
            data.push(value);
            data.push(value);
            var option = {
                backgroundColor:'',
                title: {
                    text: '总在线率',
                    left:"center",
                    textStyle: {
                        fontWeight: '400',
                        fontSize:19,
                        color:'#fff'//rgb(97, 142, 205)
                    },
                    top:"5%"
                },
                grid: {
                    top: "40%",
                    left: "center",
                    right: "",
                    bottom: "",
                    borderColor: "#012f4a",
                    containLabel: true
                },
                series: [{
                    type: 'liquidFill',
                    radius: '58%',
                    data: data,
                    backgroundStyle: {
                        borderWidth: 5,
                        borderColor: 'rgb(255,0,255,0.9)',//里面圈的  颜色
                        color: 'rgb(255,0,255,0.01)'
                    },
                    label: {
                        normal: {
                            formatter: (value * 100).toFixed(2) + '%',
                            textStyle: {
                                fontSize:30,
                                color:"#fff"
                            }
                        }
                    }
                }]
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

</style>