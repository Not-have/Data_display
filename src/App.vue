<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
    name: 'App',
    created() {
        /*
        var sUserAgent = navigator.userAgent;
        if (!!sUserAgent.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/) ){
            // ios
            document.write("<script type='text/javascript' src='http://injection/www/cordova.js'><\/script>");
            document.write("<script type='text/javascript' src='http://injection/www/cordova_plugins.js'><\/script>");

        } else if(sUserAgent.indexOf('Android') > -1 || sUserAgent.indexOf('Adr') > -1){
            // 安卓
            document.write("<script type='text/javascript' src='http://injection/www/cordova.js'><\/script>");
        }
        */
    },
}
</script>
<style>
    body,p,ul,ol,dl,dd,h1,h2,h3,h4,h5,h6,hr,td,input,textarea,fieldset,legend{
        margin:0;
        padding:0;
    }
    ul,ol,li{
        list-style:none;
    }
    a{
        text-decoration:none;
    }
    img{
        /* vertical-align: top; */
        display:block;
        border:none;/* 去掉IE浏览器下，图片的三像素 */
    }
    body{
        /* font-family:"microsoft yahei";微软雅黑,做移动端的时候 不要设置字体类型 */
        font-size:16px;/*字体大小   也可以不设置*/
        line-height: 1.15;
        font-family: Arial, Helvetica, sans-serif;
    }
    input,textarea,select,area{
        outline:none;
    }
    h1,h2,h3,h4,h5,h6,b,strong{
        font-weight: normal;
    }
    i,em{
        font-style: normal;
    }
    b{
        font-weight:normal;
    } 
    /* 在这给一个屏幕约束 */
    @media screen and (max-width:768px) {
        html {
            font-size: 80px !important;
        }
    }
    @media screen and (min-width: 1920) {
        html {
            font-size: 80px !important;
        }
    }
</style>
