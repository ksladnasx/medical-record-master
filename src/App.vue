<script setup lang="ts">
import { useRouter } from 'vue-router';
// import { useUserStore } from './store';
import Sidebar from './components/Sidebar.vue';
import { useUserStore } from './store';
import Topbar from './components/Topbar.vue';


// 路由器实例
const router = useRouter();
// 用户存储
// const userStore = useUserStore();

// 判断当前路由是否需要显示侧边栏
const shouldShowSidebar = () => {
  const publicRoutes = ['Login', 'Register', 'ForgotPassword', 'Email', 'Wrong', 'Editor', 'FileEditor'];
  return !publicRoutes.includes(router.currentRoute.value.name as string);
};

</script>

<template>
  <Topbar v-if="shouldShowSidebar() && useUserStore().shouldShowTopbar" />
  <div class="app-container">

    <!-- 只在非登录/注册/找回密码页面显示侧边栏 -->
    <Sidebar v-if="shouldShowSidebar() && useUserStore().shouldShow" />


    <div class="main-content" :class="{ 'with-sidebar': shouldShowSidebar() }">

      <div v-if="! useUserStore().shouldShowTopbar" style="display: flex; position: relative;justify-self: center;min-height: 20vh;"><el-button @click="() => useUserStore().shouldShowTopbar = true"><el-icon>
            <ArrowDownBold />
          </el-icon></el-button></div>
      <router-view v-slot="{ Component }" style="flex: 1;">
        <transition name="fade" mode="out-in">
          <component :is="Component" />

        </transition>
      </router-view>

    </div>
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
  background-color: #f5f7fa;
  width: 100%;
  height: 100%;
  overflow: visible;

}

button:focus {
  outline: none;
}

.app-container {
  width: 100%;
  height: 100vh;
  overflow: visible;
  display: flex;
  flex: 1;

}

.showSiderbar {
  position: relative;
  /* top: 15vh;
 padding-right: 100px; */
}

.main-content {
  flex: 1;
  /* overflow-y: auto; */
  transition: all 0.3s ease;
  height: auto;
 

}

/* .main-content.with-sidebar {
  width: calc(100% - 250px);
} */

/* 过渡效果 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* 滚动条样式 */
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb {
  background: #c0c4cc;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #909399;
}

.main-content {
  height: 100vh;
  /* overflow-y: auto; */
  transition: all 0.3s ease;
  /* 新增背景色设置 */
  background: linear-gradient(to right,
      rgba(245, 247, 250, 0.8) 0%,
      /* 与侧边栏渐变色衔接 */
      rgba(245, 247, 250, 1) 250px,
      /* 渐变终止点与侧边栏宽度匹配 */
      #ffffff 100%
      /* 主内容区底色 */
    );
  box-shadow: -2px 0 8px rgba(0, 0, 0, 0.05);
  /* 增加左侧分割阴影 */
}

/* 适配侧边栏隐藏状态 */
.main-content:not(.with-sidebar) {
  background: #ffffff;
  /* 纯白背景 */
  box-shadow: none;
}

/* 优化过渡动画背景 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
  background: inherit;
  /* 保持背景继承 */
}
</style>