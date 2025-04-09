<script setup lang='ts'>
// import { ref } from 'vue';
import { useRouter } from 'vue-router';
import { useUserStore } from '../store';
import { onMounted, ref } from 'vue';
import { DArrowRight, DArrowLeft } from '@element-plus/icons-vue';
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
    useUserStore().shouldShow = !useUserStore().shouldShow;
}
</script>

<template>
    <div class="main-container">
        <div class="logo">
            <svg t="1744207789193" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                p-id="1461" width="50" height="50">
                <path
                    d="M778.26048 40.96h-532.48a61.50144 61.50144 0 0 0-61.44 61.44v778.24a20.48 20.48 0 0 0 20.48 20.48h614.4a20.48 20.48 0 0 0 20.48-20.48V102.4a61.50144 61.50144 0 0 0-61.44-61.44z"
                    fill="#ECEFF8" p-id="1462"></path>
                <path
                    d="M819.24096 860.16H204.8a20.48 20.48 0 0 0-20.48 20.48v40.96a61.50144 61.50144 0 0 0 61.44 61.44h532.50048a61.50144 61.50144 0 0 0 61.44-61.44v-40.96a20.48 20.48 0 0 0-20.48-20.48zM428.38016 770.048l-35.00032-80.22016A181.61664 181.61664 0 0 0 409.62048 614.4a184.32 184.32 0 1 0-184.32 184.32h184.32a20.48 20.48 0 0 0 18.75968-28.672z"
                    fill="#6EA5FF" p-id="1463"></path>
                <path d="M512.02048 133.12m-30.72 0a30.72 30.72 0 1 0 61.44 0 30.72 30.72 0 1 0-61.44 0Z" fill="#6EA5FF"
                    p-id="1464"></path>
                <path
                    d="M286.72 593.92H163.84a20.48 20.48 0 1 1 0-40.96h122.88a20.48 20.48 0 1 1 0 40.96zM286.72 675.84H163.84a20.48 20.48 0 1 1 0-40.96h122.88a20.48 20.48 0 1 1 0 40.96z"
                    fill="#ECEFF8" p-id="1465"></path>
                <path
                    d="M471.04 286.72h-184.32a20.48 20.48 0 1 1 0-40.96h184.32a20.48 20.48 0 1 1 0 40.96zM471.04 389.12h-122.88a20.48 20.48 0 0 1 0-40.96h122.88a20.48 20.48 0 1 1 0 40.96zM737.30048 798.72h-225.28a20.48 20.48 0 0 1 0-40.96h225.28a20.48 20.48 0 1 1 0 40.96z"
                    fill="#D7DCEF" p-id="1466"></path>
                <path
                    d="M550.8096 263.74144a20.45952 20.45952 0 0 1 28.75392 0.18432l131.2768 131.21536a20.48 20.48 0 0 1-1.16736 30.02368l-143.36 122.83904a20.48 20.48 0 0 1-33.792-15.5648V307.28192a60.14976 60.14976 0 0 1 18.28864-43.52zM804.74112 395.14112l131.2768-131.21536a20.45952 20.45952 0 0 1 28.75392-0.2048A60.14976 60.14976 0 0 1 983.04 307.28192V532.48a20.48 20.48 0 0 1-33.792 15.54432l-143.36-122.83904a20.48 20.48 0 0 1-1.14688-30.0032z"
                    fill="#6EA5FF" p-id="1467"></path>
                <path
                    d="M539.68896 516.9152l143.36-122.83904a20.48 20.48 0 0 1 27.79136 1.06496L757.76 442.10176l46.96064-46.91968a20.45952 20.45952 0 0 1 27.79136-1.08544l143.36 122.83904a20.48 20.48 0 0 1 7.14752 15.54432v20.48a61.48096 61.48096 0 0 1-61.44 61.39904h-156.63104l-96.768 77.4144a20.48 20.48 0 0 1-33.28-15.99488v-61.41952h-40.96a61.48096 61.48096 0 0 1-61.44-61.41952v-20.48a20.48 20.48 0 0 1 7.168-15.52384z"
                    fill="#D7DCEF" p-id="1468"></path>
                <path
                    d="M880.5376 435.2l-48.00512-41.12384a20.45952 20.45952 0 0 0-27.79136 1.06496l-46.96064 46.94016-46.94016-46.94016a20.48 20.48 0 0 0-27.81184-1.06496l-47.98464 41.12384 79.29856 79.27808a61.41952 61.41952 0 0 0 86.89664 0z"
                    fill="#6EA5FF" p-id="1469"></path>
                <path
                    d="M550.42048 264.11008a60.29312 60.29312 0 0 1 43.54048-18.26816H921.6a60.29312 60.29312 0 0 1 43.56096 18.26816 20.48 20.48 0 0 1-0.2048 28.75392l-192.69632 192.65536a20.48 20.48 0 0 1-28.95872 0L550.62528 292.864a20.48 20.48 0 0 1-0.2048-28.75392z"
                    fill="#D7DCEF" p-id="1470"></path>
            </svg>
            <div style="padding-left: 30px;">
                <h2 style="font-size: 5vh;">电子病历撰写系统</h2>
            </div>

            <span v-if="useUserStore().shouldShow" class="hidden-sidebar" @click="hiddenSidebar" title="收起侧边栏">
                <el-icon class="fullscreen">
                    <DArrowLeft />
                </el-icon>

            </span>
            <span v-if="!useUserStore().shouldShow" class="hidden-sidebar" @click="hiddenSidebar" title="展开侧边栏">
                <el-icon class="fullscreen">
                    <DArrowRight />
                </el-icon>
            </span>
            <span style="padding-left:5vh; ">
                <el-button @click="()=>useUserStore().shouldShowTopbar = false" style="background-color: transparent;border: 0px none;"><el-icon size="large"
                        style="color: aliceblue;">
                        <FullScreen />
                    </el-icon></el-button>
            </span>
        </div>
        <div class="user-info">
            <div class="avatar-container">
                <div class="avatar">
                    <img :src=src alt="User Avatar" @click="navigateToProfile" title="个人信息" />
                </div>
                <div class="user-name">{{ userStore.$state.userInfo?.userName }}</div>
            </div>
            <div class="logout" @click="logout" title="退出登录">
                <div>
                    <i class="el-icon-switch-button">
                        <svg t="1744190528338" class="icon" viewBox="0 0 1024 1024" version="1.1"
                            xmlns="http://www.w3.org/2000/svg" p-id="2635" width="4vh" height="4vh">
                            <path
                                d="M649.813333 808.533333L576 878.933333c-11.52 11.093333-26.88 17.066667-42.666667 17.066667H250.026667C206.08 896 170.666667 860.586667 170.666667 816.64V207.36C170.666667 163.413333 206.08 128 250.026667 128h281.6c16.64 0 32.426667 6.4 43.946666 18.346667l70.826667 70.826666a42.496 42.496 0 1 0 60.16-60.16L635.733333 85.76A146.56 146.56 0 0 0 531.626667 42.666667h-281.6C159.146667 42.666667 85.333333 116.48 85.333333 207.36v609.706667A164.693333 164.693333 0 0 0 250.026667 981.333333h283.306666c37.973333 0 74.24-14.506667 101.546667-40.533333l73.813333-69.973333c17.066667-16.213333 17.92-43.093333 1.706667-60.16a42.666667 42.666667 0 0 0-60.586667-2.133334z"
                                p-id="2636" fill="#bfbfbf"></path>
                            <path
                                d="M951.893333 481.706667l-143.786666-143.786667a42.496 42.496 0 1 0-60.16 60.16L818.773333 469.333333H412.586667c-23.466667 0-42.666667 19.2-42.666667 42.666667s19.2 42.666667 42.666667 42.666667h406.186666l-70.826666 70.826666a42.496 42.496 0 0 0 30.293333 72.533334c11.093333 0 21.76-4.266667 30.293333-12.373334l143.786667-143.786666c16.213333-16.213333 16.213333-43.52-0.426667-60.16z"
                                p-id="2637" fill="#bfbfbf"></path>
                        </svg>
                    </i>
                </div>

                <div style=" font-size:15px;display: inline;">退出登录</div>
            </div>

            <div class="user-details">

            </div>

        </div>

    </div>
</template>



<style scoped>
.main-container {
    height: 9vh;
    background: linear-gradient(to right, #0062ff, #245da8);
    color: #ecf0f1;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    padding-left: 20px;
    transition: width 0.3s ease;
}

.logo {
    display: flex;
    align-items: center;
    height: 60px;

}

.hidden-sidebar {
    color: #ffffff;
    border-radius: 50%;
    cursor: pointer;
    font-size: 28px;
    padding-top: 2px;
    display: flex;
    flex-direction: column;
    ;
    align-items: center;
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

.user-info {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 200px;
}

.avatar-container {
    display: flex;
    flex-direction: column;
    /* align-items: center;  */
    justify-content: center;
}

.avatar {
    width: 6vh;
    height: 6vh;
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
    font-size: 2vh;
    font-weight: bold;
    padding-left: 9px;
}

.user-role {
    font-size: 12px;
    color: #ccc;
}

.logout {
    cursor: pointer;
    display: flex;

    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    padding-left: 6vh;
    transition: all 0.3s ease;
}

.logout:hover {
    color: #ff6b6b;
    transform: scale(1.2);
}
</style>