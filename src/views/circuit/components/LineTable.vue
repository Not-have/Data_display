<!-- 
 * @FileDescription:线路详细信息的表格
 * @Author: 李勇
 * @Date: 2020-07-23    15:28
 * @LastEditors: 
 * @LastEditTime: 
-->
<template>
    <div class="table">
        <el-table :data="tableData" height="4.2rem" border style="width:90%">
            <el-table-column prop="date" label="日期" width="180"></el-table-column>
            <el-table-column prop="name" label="姓名" width="180"></el-table-column>
            <el-table-column prop="address" label="地址"></el-table-column>
        </el-table>
    </div>
</template>
<script>
export default {
  data() {
    return {
        tableData: [
            {
                date: "2016-05-03",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-02",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-04",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-01",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-08",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-06",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
            {
                date: "2016-05-07",
                name: "王小虎",
                address: "上海市普陀区金沙江路 1518 弄",
            },
        ],
    };
  },
};
</script>
<style lang="scss" scoped>
    .table{
        width:100%;
        margin-left:5%;
    }
</style>