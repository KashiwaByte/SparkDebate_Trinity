<script setup>
import { reactive, watch, ref, onMounted, onUnmounted } from 'vue';
import ExploreAI from './Sub/ExploreAI.vue';
import CreateAI from './Sub/CreateAI.vue'
import CheckAllSession from './Sub/CheckAllSession.vue'
import Session from './Sub/Session.vue'
import DebateTrain from './Sub/DebateTrain.vue'
import DebateMatch from './AIMatch/DebateMatch.vue'
import AIDebateCompetition from './Sub/AIDebateCompetition.vue';
const state = reactive({
  // 探索AI助手, 创造AI助手, 查看所有聊天记录, 对话
  mode: 'AI辩论训练',

  index_session_chosen: 0,
  sessionList: [{
    session_id: 123,
    avatar_url: '',
    ai_name: 'TBRLIS',
    brief: '西电湖人你是真的火了'
  }, {
    session_id: 124,
    avatar_url: '',
    ai_name: '西电辩手',
    brief: '人工智能学院辩论队赛高'
  }]
})

const modeList = [
  {
    name: '探索AI助手',
  },
  {
    name: '创造AI助手',
  }
]

const navList = [
  {
    name: '首页',
  },
  {
    name: 'AI辩论训练',
  },
  {
    name: 'AI辩论赛事',
  },
  {
    name:"赛事发布"
  }
]

const chooseSession = (index) => {
  state.index_session_chosen = index
  state.mode = '对话'
}

const clickNav = (name) => {
  if(name === 'AI辩论训练') {
    state.mode = 'AI辩论训练'
  }
  else if(name === '赛事发布') {
    state.mode = '赛事发布'
  } else if(name === 'AI辩论赛事') {
    state.mode = 'AI辩论赛事'
  }
}

// 调整滚动条位置, 使得居中
const scrollableArea = ref(null);
let observer;
const adjustScroll = () => {
  const scrollable = scrollableArea.value.$el.querySelector('.el-scrollbar__wrap');
  if (scrollable) {
    scrollable.scrollLeft = (scrollable.scrollWidth - scrollable.clientWidth) / 2;
  }
};
onMounted(() => {
  observer = new ResizeObserver(adjustScroll);
  observer.observe(scrollableArea.value.$el.querySelector('.el-scrollbar__wrap'));
});
onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});

// 监听模式变化
watch(() => state.mode, (val) => {
  console.log(val);
  if(val === '探索AI助手') {
    setTimeout(() => {
      adjustScroll()
    }, 100)
  }
})
</script>

<template>
  <div class="main-box">
    <div class="header">
      <div @click="clickNav(item.name)" class="tab" v-for="item in navList" :key="item.name">{{ item.name }}</div>
      <el-avatar class="avatar" :size="53" :src="1">
          <img
            src="/avatarDefault.png"
          />
      </el-avatar>
    </div>
     <DebateMatch v-if="state.mode === '赛事发布'" style="z-index:99"></DebateMatch>
    <!-- aside和main -->
    <div class="mid" v-else>
      <div class="aside">
        <!-- 模式选择 -->
        <div class="modeChangeBox">
          <div class="button" v-for="mode in modeList" :key="mode" @click="state.mode = mode.name">{{ mode.name }}</div>
        </div>
        <!-- 可选会话列表 -->
        <el-scrollbar class="list">
          <div @click="chooseSession(i)" :class="['session', 'chosen'?state.index_session_chosen == i:'']" v-for="(session, i) in state.sessionList" :key="session.session_id">
            <el-avatar :size="53" :src="session.avatar_url">
              <img
                src="/avatarDefault.png"
              />
            </el-avatar>
            <div class="info">
              <div class="name">{{ session.ai_name }}</div>
              <div class="brief">{{ session.brief }}</div>
            </div>
            <el-icon class="arrow" v-if="state.index_session_chosen == i" color="#ffffff" size="45"><ArrowRightBold/></el-icon>
          </div>
        </el-scrollbar>
        <!-- 查看所有聊天记录按钮 -->
        <div class="checkAllSession" @click="state.mode = '查看所有聊天记录'">
          查看所有聊天记录
        </div>
      </div>
      <el-scrollbar ref="scrollableArea" class="main">
        <ExploreAI v-if="state.mode === '探索AI助手'"></ExploreAI>
        <CreateAI v-else-if="state.mode === '创造AI助手'"></CreateAI>
        <CheckAllSession v-else-if="state.mode === '查看所有聊天记录'"></CheckAllSession>
        <Session v-else-if="state.mode === '对话'"></Session>
        <DebateTrain v-else-if="state.mode === 'AI辩论训练'"></DebateTrain>
        <AIDebateCompetition v-else-if="state.mode === 'AI辩论赛事'"></AIDebateCompetition>
      </el-scrollbar>
    </div>
  </div>
 
</template>
  

<style lang="scss" scoped>
// 颜色
$deepPurple: #7565C6;
$lightPurple: #8775DD;
$navFontColor: #ffffff;
$hoverGray: #cccccc;
// 布局
$headerHeight: 80px;
$asideWidth: 306px;
$halfWidth: 1000px;
.header {
  background-color: $deepPurple;
  height: $headerHeight;

  display: flex;
  align-items: center;
  padding-left: $asideWidth;
  @media (max-width: $halfWidth) {
   padding-left: calc($asideWidth / 9);   
  }
  position: relative;
  .tab {
    color: $navFontColor;
    margin-right: 80px;
    font-size: 28px;
    white-space: nowrap;

    &:hover {
      cursor: pointer;
      // 变蓝
      color: $hoverGray;
    }

  }
  .avatar {
    position: absolute;
    right: 25px;
  }
}

.mid {
  display: flex;
  height: calc(100vh - $headerHeight);
}

$asideItemWidth: 130px;
$asideBorderRadius: 20px;
$gap: 5px;
.aside {
  background-color: $deepPurple;
  width: $asideWidth;
  height: 100%;
  padding: 0 19px 0px 15px;
  .modeChangeBox {
    height: 148px;
    border-radius: $asideBorderRadius $asideBorderRadius 0 0;
    background-color: $lightPurple;
    padding: 0 14px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    .button {
      width: $asideItemWidth;
      height: 81px;
      border-radius: 20px;
      font-size: 18px;
      
      font-weight: bold;
      background-color: $deepPurple;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #ffffff;
      &:hover {
        cursor: pointer;
        color: $hoverGray;
      }
    }

  }
  .list {
    height: 532px;
    background-color: $lightPurple;
    margin-bottom: $gap;
    .session {
      &:first-child {
        border-top: $gap $deepPurple solid;
      }
      background-color: $lightPurple;
      // margin-top: 5px;
      border-bottom: $gap $deepPurple solid;
      height: 145px;
      display: flex;
      align-items: center;
      padding-left: 15px;
      .info {
        margin-left: 10px;
        display: flex;
        flex-direction: column;
        
        .name {
          font-size: 28px;
          font-family: SourceHanSansSC-regular;
          color: #363636 100%;
          font-weight: 700;
        }
        .brief {
          font-size: 14px;
          color: #363636 100%;
          font-family: SourceHanSansSC-medium;
        }
      }
      .arrow {
        margin-left: auto;
        margin-right: 5px;
      }
      &:hover {
        cursor: pointer;
      }
    }
  }

  .checkAllSession {
      background-color: $lightPurple;
      height: 81px;
      border-radius: 0 0 20px 20px;
      font-size: 18px;
      font-weight: bold;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #ffffff;
      white-space: nowrap;
      &:hover {
        cursor: pointer;
        color: $hoverGray;
      }
    }
}

.main {
  background-color: #F3F5F8;
  flex: 1;
  overflow: hidden;
}

</style>