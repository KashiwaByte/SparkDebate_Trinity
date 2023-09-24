<script setup>
import { reactive} from 'vue';
const state = reactive({
    isSupportAuditing: false
})
</script>

<template>
    <div class="container">

    
    <div class="body">
        <div class="title">
            赛事发布
        </div>
        <div class="content">
                <div class="line" >
                 <div class="left">辩题：</div>
                 <div class="right">
                     <input type="text">
                 </div>
            </div>
            <div class="line" >
                 <div class="left">赛事码：</div>
                 <div class="right"><input type="text"></div>
            </div>
            <div class="mid">
                <div class="box-left">
                    参赛成员：
                </div>
                <div>
                     <div class="box">
                        <div class="item-line">
                            <div class="item">正方总辩手：
                                <input type="text">
                            </div>
                             <div class="item">正方AI辩手：
                                <input type="text">
                            </div>
                          
                        </div> 
                    <div class="item-line">
                        <div class="item">正方AI辩手：
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>     
                    </div>
                    </div>
                    <div class="box">
                        <div class="item-line">
                            <div class="item">反方总辩手：
                                <input type="text">
                            </div>
                             <div class="item">反方AI辩手：
                                <input type="text">
                            </div>
                          
                        </div> 
                    <div class="item-line">
                        <div class="item">反方AI辩手：
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>
                            <div class="item">
                                <div class="small-item">TABRIS</div>
                            </div>     
                    </div>
                    </div>
                </div>
                  
            </div>
             <div class="line" >
                 <div class="left" style="width:120px">比赛时间：</div>
                 <div class="right" style="margin-left:16px"><input type="text" style="width: 325px;"></div>
            </div> 
            <div class="line" >
                 <div class="left" style="width:120px">赛事名称：</div>
                 <div class="right" style="margin-left:16px"><input type="text" style="width: 590px;"> </div>
            </div>
             <div class="line" >
                 <div class="left" style="width:120px">房间密码：</div>
                 <div class="right" style="margin-left:16px"><input type="text" style="width: 325px;"></div>
            </div>
               <div class="line" >
                 <div class="left" style="width:120px">支持旁听：</div>  
                 <div><el-switch size="large" class="switch" active-color="#7565C6" v-model="state.isSupportAuditing"/></div>
            </div>
        </div>
        <div class="submit">
            <div class="text">发布</div>
            
        </div>
    </div>
</div>
</template>

<style lang="scss" scoped>
$deepPurple: #7565C6;
$lightPurple: #8775DD;
$navFontColor: #ffffff;
$hoverGray: #cccccc;
// 布局
$halfWidth: 1000px;


.switch {
    margin-left: 274px;
}
.container {
    width: 100%;
    background-color: $deepPurple;
    border-top: 1px solid #fff;
}
.body{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 837px;
    margin: 0 auto;
    background-color: #fff;
    .title{
        margin-top:25px;
        width: 160px;
        height: 53px;
        color: rgba(117, 101, 198, 1);
        font-size: 40px;
        text-align: left;
        font-family: OPPOSans-medium;
    }
    .content{
        display: flex;
        flex-direction: column;
         .line{
            margin-top:30px;
        display: flex;
        align-items: center;
        .left{
            width: 100px;
            height: 35px;
            color: rgba(52, 51, 51, 1);
            font-size: 24px;
            text-align: left;
            font-family: SourceHanSansSC-regular;
        }
        .right{
           box-sizing: border-box;
            margin-left: 36px;
            width: 589px;
            height: 50px;
            // border-radius: 5px;
            // background-color: rgba(255, 255, 255, 1);
            // text-align: center;
            input{
                width: 98.5%;
                height: 100%;
               border: 2px solid rgba(135, 117, 221, 1);
               border-radius: 5px;
            }
            input:focus {
                   border-color: rgba(135, 117, 221, 1);
                outline-color: rgba(135, 117, 221, 1);
        }
         }
     }
     .mid{
        display: flex;
        align-items: center;
        .box-left{
            width: 120px;
            height: 35px;
            color: rgba(52, 51, 51, 1);
            font-size: 24px;
            text-align: left;
            font-family: SourceHanSansSC-regular;
        }
         .box{
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            padding-left: 25px;
            padding-right: 25px;
            margin-top: 28px;
             margin-left: 16px;
            width: 589px;
            height: 90px;
            line-height: 20px;
            border-radius: 5px;
            background-color: rgba(211, 205, 240, 1);
            text-align: center;
            .item-line{
                display: flex;
                justify-content: space-between;
                margin-left: 25px;
                margin-top:13px;
                .item{
                display: flex;
                align-items: center;
                height: 26px;
                color: rgba(16, 16, 16, 1);
                font-size: 18px;
                text-align: left;
                font-family: SourceHanSansSC-regular;
                    input{
                        width: 72px;
                        height: 30px;
                        line-height: 20px;
                        font-size: 14px;
                        font-family: Roboto;
                          border: 2px solid rgba(135, 117, 221, 1);
                          border-radius: 5px;
                    }
                      input:focus {
                         border-color: rgba(135, 117, 221, 1);
                         outline-color: rgba(135, 117, 221, 1);
                  }
                  .small-item{
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    width: 80px;
                    height: 30px;
                    line-height: 20px;
                    border-radius: 5px;
                    background-color: rgba(255, 255, 255, 1);
                    text-align: center;
                    border: 1px solid rgba(135, 117, 221, 1);
                  }
            }
           
        }
     }
       
    }
  
 }
 .submit{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 140px;
        height: 60px;
        border-radius: 69px;
        background-color: rgba(135, 117, 221, 1);
        text-align: center;
        .text{
        color: rgba(255, 255, 255, 1);
        font-size: 24px;
        font-family: SourceHanSansSC-regular;
    }
    }
   
}
</style>