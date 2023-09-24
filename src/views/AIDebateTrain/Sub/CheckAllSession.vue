<script setup>

</script>

<template>
        <div class="title">
            你的聊天记录
        </div>
        <div class="content">
            <div class="item" v-for="count in 1">
                <img src="/avatarDefault.png" >
                <div class="name">
                    TABRIS
                </div>
                <div class="saying">
                    第十三使徒塔布里斯自由天使。
                </div>
                <div class="arrow">
                    <el-icon color="#7565C6" size="40"><ArrowRightBold/></el-icon>
                </div>
            </div>
        </div>
        <div class="content">
            <div class="item" v-for="count in 1">
                <img src="/avatarDefault.png" >
                <div class="name">
                    kashiwa1
                </div>
                <div class="saying">
                    明日香是最好看的。
                </div>
                <div class="arrow">
                    <el-icon color="#7565C6" size="40"><ArrowRightBold/></el-icon>
                </div>
            </div>
        </div>
        <div class="content">
            <div class="item" v-for="count in 1">
                <img src="/avatarDefault.png" >
                <div class="name">
                    wt1
                </div>
                <div class="saying">
                    凌波丽是最好看的。
                </div>
                <div class="arrow">
                    <el-icon color="#7565C6" size="40"><ArrowRightBold/></el-icon>
                </div>
            </div>
        </div>
</template>

<style lang="scss" scoped>
.title{
    position: relative;
    left: 454px;
    top: 69px;
    width: 240px;
    height: 53px;
    color: rgba(117, 101, 198, 1);
    font-size: 40px;
    text-align: left;
    font-family: OPPOSans-medium;
}
.content{
    position: relative;
    left: 179px;
    top: 94px;
    width: 795px;
    .item{
        position: relative;
        width: 795px;
        height: 100px;
        line-height: 20px;
        background-color: rgba(255, 255, 255, 1);
        color: rgba(16, 16, 16, 1);
        font-size: 14px;
        text-align: center;
        font-family: Roboto;
        margin-bottom: 5px;
        img{
            position: absolute;
            left: 15px;
            top: 11px;
            width: 75px;
            height: 75px;
        }
        .name{
            position: absolute;
            left: 109px;
            top: 20px;
            width: 69px;
            height: 30px;
            color: rgba(16, 16, 16, 1);
            font-size: 20px;
            text-align: left;
            font-family: SourceHanSansSC-medium;
        }
        .saying{
            position: absolute;
            left: 109px;
            top: 55px;
            width: 196px;
            height: 20px;
            color: rgba(16, 16, 16, 1);
            font-size: 14px;
            text-align: left;
            font-family: SourceHanSansSC-regular;

        }
        .arrow{
            position: absolute;
            right: 14px;
            top: 30px;
        }
    }
}
</style>