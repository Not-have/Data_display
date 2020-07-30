<template>
    <div class="dashboard">
        <Current />
        <div class="mainbox">
            <div class="column">
                <NewHitch />
                <Broken />
                <Customized />
            </div>
            <div class="column">
                <Character />
            </div>
            <div class="column">
                <Terminus />
                <NewTerminal /> 
                <TerminalTyoes />
            </div>
        </div>
    </div>
</template>

<script>
//引入vuex里面的数据
import { mapGetters } from 'vuex'
import Current from "./components/Current.vue"; 
import NewHitch from "./components/Newhitch.vue";
import Broken from "./components/Broken.vue";
import Customized from "./components/Customized.vue";
import Character from "./components/Character.vue";
import Terminus from "./components/Terminus.vue";
import NewTerminal from "./components/NewTerminal.vue";
import TerminalTyoes from "./components/TerminalTypes.vue";
export default {
    name: 'Dashboard',
    //计算属性
    computed: {
        
    },
    components:{
        Current,
        NewHitch,
        Broken,
        Customized,
        Character,
        Terminus,
        NewTerminal,
        TerminalTyoes
    }
}
</script>

<style lang="scss" scoped>
    @media screen and (min-width:992px) {
        .dashboard {
            width:100%;
            // 最大时这些
            min-height: calc(100vh - 50px);
            box-sizing:border-box;
            background: url("~@/assets/images/bg.jpg") no-repeat #000;
            background-size: cover;
        }
        .mainbox {
            box-sizing: border-box;
            padding: .12rem;
            padding-top:.06rem;
            display: flex;
            height:100%;
            .column {
                height:100%;
                flex: 3;
                &:nth-child(2){
                    flex: 5;
                    margin-left:.1rem;
                    margin-right:.1rem;
                }
            }
        }
    }
    @media screen and (max-width:768px) {
        .dashboard {
            width:100%;
            // 最大时这些
            min-height: calc(100vh - 50px);
            box-sizing:border-box;
            background: url("~@/assets/images/bg.jpg") no-repeat #000;
            background-size: cover;
        }
        .mainbox {
            box-sizing: border-box;
            padding-top:.06rem;
            height:100%;
            .column {
                height:100%;
            }
        }
    }
</style>
