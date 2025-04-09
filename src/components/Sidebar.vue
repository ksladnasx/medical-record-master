<script setup lang="ts">
// import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useUserStore } from '../store';
import { useRoute } from 'vue-router'
import { onMounted, ref } from 'vue';
import { User, Notebook, Document, Unlock, DArrowLeft } from '@element-plus/icons-vue';
const route = useRoute()
// 路由器实例
const router = useRouter();
// 用户存储
const userStore = useUserStore();
// 活动菜单项索引
// const activeIndex = ref('1');
const src = ref("https://tse3-mm.cn.bing.net/th/id/OIP-C.JCEcaQJVR_vC2kgt6BGZlAAAAA?rs=1&pid=ImgDetMain");

onMounted(() => {
  const userInfo = localStorage.getItem('userInfo');
  if (userInfo) {
    src.value = JSON.parse(userInfo).avatarUrl;
  }
});
// 导航到指定路径
const navigateTo = (path: string) => {
  router.push(path);
};

// 跳转到个人信息
const navigateToProfile = () => {
  router.push('/setting');
};

// 登出
const logout = () => {
  userStore.logout();
  router.push('/login');
};
const hiddenSidebar = () => {
  useUserStore().shouldShow = false;
}
</script>

<template>
  <div v-if="!route.path.includes('/Editor') && !route.path.includes('/FileEditor')" class="sidebar">
    <div class="logo">
      <h2>电子病历撰写系统</h2>
      
      <span class="hidden-sidebar" @click="hiddenSidebar">
        <el-icon class="fullscreen">
        <DArrowLeft />
      </el-icon>
      </span>
    </div>

    <div class="user-express">
      <div class="main-avatar">
        <img :src=src alt="User Avatar" class="icon" @click="navigateToProfile" />
      </div>
      <p></p>
      <div style="width: 86px; text-align: center;">{{ userStore.$state.userInfo?.userName }}
      </div>
    </div>


    <div class="menu">

      <div class="menu-item" @click="navigateTo('/modelfile')" :class="{ active: route.path === '/modelfile' }">
        <el-icon>
          <Notebook />
        </el-icon>
        <span>模板管理</span>
      </div>

      <div class="menu-item" @click="navigateTo('/filemanage')" :class="{ active: route.path === '/filemanage' }">
        <el-icon>
          <Document />
        </el-icon>
        <span>文件管理</span>
      </div>

      <div class="menu-item" @click="navigateTo('/permissions')" :class="{ active: route.path === '/permissions' }">
        <el-icon>
          <Unlock />
        </el-icon>
        <span>权限管理</span>
      </div>

      <div class="menu-item" @click="navigateTo('/setting')" :class="{ active: route.path === '/setting' }">
        <el-icon>
          <User />
        </el-icon>
        <span>用户设置</span>
      </div>
    </div>

    <div class="user-info">
      <div class="avatar">
        <img :src=src alt="User Avatar" @click="navigateToProfile" title="个人信息" />
      </div>
      <div class="user-details">
        <div class="user-name">{{ userStore.$state.userInfo?.userName }}</div>
        <div class="user-role">{{ userStore.$state.userInfo?.organization }}</div>
      </div>
      <div class="logout" @click="logout" title="退出登录">
        <i class="el-icon-switch-button">
          <svg t="1744190528338" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
            p-id="2635" width="200" height="200">
            <path
              d="M649.813333 808.533333L576 878.933333c-11.52 11.093333-26.88 17.066667-42.666667 17.066667H250.026667C206.08 896 170.666667 860.586667 170.666667 816.64V207.36C170.666667 163.413333 206.08 128 250.026667 128h281.6c16.64 0 32.426667 6.4 43.946666 18.346667l70.826667 70.826666a42.496 42.496 0 1 0 60.16-60.16L635.733333 85.76A146.56 146.56 0 0 0 531.626667 42.666667h-281.6C159.146667 42.666667 85.333333 116.48 85.333333 207.36v609.706667A164.693333 164.693333 0 0 0 250.026667 981.333333h283.306666c37.973333 0 74.24-14.506667 101.546667-40.533333l73.813333-69.973333c17.066667-16.213333 17.92-43.093333 1.706667-60.16a42.666667 42.666667 0 0 0-60.586667-2.133334z"
              p-id="2636" fill="#bfbfbf"></path>
            <path
              d="M951.893333 481.706667l-143.786666-143.786667a42.496 42.496 0 1 0-60.16 60.16L818.773333 469.333333H412.586667c-23.466667 0-42.666667 19.2-42.666667 42.666667s19.2 42.666667 42.666667 42.666667h406.186666l-70.826666 70.826666a42.496 42.496 0 0 0 30.293333 72.533334c11.093333 0 21.76-4.266667 30.293333-12.373334l143.786667-143.786666c16.213333-16.213333 16.213333-43.52-0.426667-60.16z"
              p-id="2637" fill="#bfbfbf"></path>
          </svg>
        </i>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  -webkit-user-select: none;
  /* Chrome/Safari/Edge */
  -moz-user-select: none;
  /* Firefox */
  -ms-user-select: none;
  /* IE10+ */
  user-select: none;
  /* 标准语法 */
}

.logo {
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  border-bottom: 1px solid #1f2d3d;
  background-color: #263445;
}
.hidden-sidebar{
  color: #ffffff;
  border-radius: 50%; 
  /* background-color: #4ec8e0; */
  cursor: pointer; 
  /* cursor: pointer设置鼠标挪动到此的时候改变鼠标状态 */
  font-size: 28px;
  padding-top: 2px;
  display: flex;
  align-items: center;
  /* justify-content: center; */
  position: relative;
  left: 15px;
  transition: all 0.3s ease;
}
.hidden-sidebar:hover {
  border: #1890ff 1px solid;
  background-color: rgba(255, 255, 255, 0.1);
  color: #ff6b6b;
  transform: scale(1.2);
}
.logo h2 {
  margin: 0;
  font-size: 18px;
  letter-spacing: 1px;
}

.menu {
  flex: 1;
  padding: 20px 0;
  overflow-y: auto;
}

.menu-item {
  height: 50px;
  display: flex;
  align-items: center;
  padding: 0 20px;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-bottom: 5px;
  border-radius: 4px;
  margin-left: 10px;
  margin-right: 10px;

}

.menu-item:hover {
  background-color: #263445;
  transform: translateX(5px);
}

.menu-item.active {
  background-color: #1890ff;
  color: white;
}

.menu-item i {
  margin-right: 10px;
  font-size: 18px;
  transition: all 0.3s ease;
}

.menu-item:hover i {
  transform: scale(1.2);
}

.user-express {
  width: 86px;
  height: 108px;
  font-size: 13px;
  /* display: flex; */
  position: relative;
  left: 70px;
  transition: all 0.3s ease;
}

.user-express:hover {
  transform: scale(1.2);
}

.user-info {
  height: 80px;
  border-top: 1px solid #1f2d3d;
  display: flex;
  align-items: center;
  padding: 0 20px;
  background-color: #263445;
}

.main-avatar {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  overflow: hidden;
  margin-right: 10px;
  border: 2px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.icon {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  overflow: hidden;
  margin-right: 10px;
  border: 2px solid rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
}

.avatar:hover {
  border-color: #1890ff;
  transform: scale(1.05);
}

.avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.user-details {
  flex: 1;
}

.user-name {
  font-size: 14px;
  font-weight: bold;
}

.user-role {
  font-size: 12px;
  color: #ccc;
}

.logout {
  cursor: pointer;
  font-size: 18px;
  padding-top: 2px;
  display: flex;
  align-items: center;
  justify-content: center;
  /* border-radius: 50%; */
  transition: all 0.3s ease;
}

.logout:hover {
  /* background-color: rgba(255, 255, 255, 0.1); */
  color: #ff6b6b;
  transform: scale(1.2);
}

.sidebar {
  width: clamp(80px, 20vw, 220px);
  /* 动态宽度，范围200-300px */
  height: 100vh;
  background-color: #304156;
  color: #fff;
  display: flex;
  flex-direction: column;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  z-index: 10;
  flex-shrink: 0;
  transition: width 0.3s ease;
  /* 添加过渡动画 */
}

.logo {
  height: clamp(50px, 8vh, 70px);
  /* 动态高度 */
  padding: 0 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #1f2d3d;
  background-color: #263445;
}

.logo h2 {
  margin: 0;
  font-size: clamp(14px, 1.5vw, 18px);
  /* 动态字体大小 */
  letter-spacing: 1px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.menu {
  flex: 1;
  padding: 2vh 0;
  overflow-y: auto;
}

.menu-item {
  height: clamp(40px, 6vh, 50px);
  /* 动态高度 */
  display: flex;
  align-items: center;
  padding: 0 clamp(10px, 1.5vw, 20px);
  margin: 0 0.5rem 0.5rem;
  font-size: clamp(12px, 1.1vw, 14px);
  /* 动态字体 */
}

.menu-item i {
  margin-right: clamp(8px, 1vw, 12px);
  font-size: clamp(16px, 1.5vw, 18px);
}

.user-express {
  width: auto;
  height: auto;
  margin: 2vh auto;
  left: 0;
  text-align: center;
}

.main-avatar {
  width: clamp(70px, 10vw, 90px);
  height: clamp(70px, 10vw, 90px);
  margin: 0 auto;
}

.user-info {
  height: clamp(60px, 8vh, 80px);
  padding: 0 clamp(10px, 1.5vw, 20px);
}

.avatar {
  width: clamp(30px, 4vw, 40px);
  height: clamp(30px, 4vw, 40px);
}

.user-name {
  font-size: clamp(12px, 1.1vw, 14px);
}

.user-role {
  font-size: clamp(10px, 0.9vw, 12px);
}

.logout {
  width: clamp(25px, 3vw, 30px);
  height: clamp(25px, 3vw, 30px);
  font-size: clamp(14px, 1.5vw, 18px);
}

.sidebar {
  width: clamp(80px, 20vw, 220px);
  height: 100vh;
  background: linear-gradient(to top, #1a73e8, #64b5f6);
  /* 从下往上的蓝色渐变 */
  color: #fff;
  display: flex;
  flex-direction: column;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  z-index: 10;
  flex-shrink: 0;
  transition: width 0.3s ease;
}

.logo {
  background: transparent;
  /* 移除原有背景色 */
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  /* 调整分割线颜色 */
}

.user-info {
  background: transparent;
  /* 移除原有背景色 */
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  /* 调整分割线颜色 */
}

.menu-item:hover {
  background-color: rgba(255, 255, 255, 0.1);
  /* 调整悬停效果 */
}

.menu-item.active {
  background: rgba(255, 255, 255, 0.2);
  /* 调整选中效果 */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  /* 添加阴影增强层次 */
}
</style>