<template>
    <div class="newline">
        <!-- 新增线路 -->
        <p class="line_title">本月新增线路</p>
        <p class="line_num">2000</p>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss" scoped>
    /*.newline {
        position: relative;
        height:3.2rem;
        border: 1px solid rgba(25, 186, 139, 0.17);
        background: rgba(255, 255, 255, 0.04) url("~@/assets/images/line.png");
        padding: 0 0.1875rem 0.5rem;
        margin-bottom: 0.1875rem;
        &::before {
            position: absolute;
            top: 0;
            left: 0;
            content: "";
            width: 10px;
            height: 10px;
            border-top: 2px solid #02a6b5;
            border-left: 2px solid #02a6b5;
        }
        &::after {
            position: absolute;
            top: 0;
            right: 0;
            content: "";
            width: 10px;
            height: 10px;
            border-top: 2px solid #02a6b5;
            border-right: 2px solid #02a6b5;
        }
        .panel-footer {
            position: absolute;
            left: 0;
            bottom: 0;
            width: 100%;
            &::before {
                position: absolute;
                bottom: 0;
                left: 0;
                content: "";
                width: 10px;
                height: 10px;
                border-bottom: 2px solid #02a6b5;
                border-left: 2px solid #02a6b5;
            }
            &::after {
                position: absolute;
                bottom: 0;
                right: 0;
                content: "";
                width: 10px;
                height: 10px;
                border-bottom: 2px solid #02a6b5;
                border-right: 2px solid #02a6b5;
            }
        }
    }*/
    .newline{
        width:50%;
        height:3rem;
        flex-direction:column;
        display: flex;
        background: rgba(255, 255, 255, 0.04) url("~@/assets/images/line.png");
        justify-content: center;
        align-items: center;
        color:white;
        .line_title{
            font-weight:400;
            font-size:.30rem;
            margin-bottom:.2rem;
        }
        .line_num{
            font-weight:400;
            font-size:.20rem;
        }
    }
</style>