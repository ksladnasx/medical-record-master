<script setup lang='ts'>
import { useRouter } from 'vue-router';
import { useUserStore } from '../store';
import { onMounted, ref } from 'vue';
import { DArrowRight, DArrowLeft, FullScreen, Rank } from '@element-plus/icons-vue';

const router = useRouter();
const userStore = useUserStore();
const src = ref("https://tse3-mm.cn.bing.net/th/id/OIP-C.JCEcaQJVR_vC2kgt6BGZlAAAAA?rs=1&pid=ImgDetMain");

onMounted(() => {
    const userInfo = localStorage.getItem('userInfo');
    if (userInfo) {
        src.value = JSON.parse(userInfo).avatarUrl;
    }
});

const navigateToProfile = () => {
    router.push('/setting');
};

const logout = () => {
    userStore.logout();
    router.push('/login');
};

const hiddenSidebar = () => {
    useUserStore().shouldShow = !useUserStore().shouldShow;
};

const FullScreens = () => {
    if (document.fullscreenElement) {
        document.exitFullscreen();
    } else {
        document.documentElement.requestFullscreen();
    }
};

const FullScreens2 = () => { 
    useUserStore().shouldShowTopbar = false; 
    useUserStore().shouldShow = false;
};
</script>

<template>
    <div class="main-container">
        <div class="logo-container">
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
                <div class="title">
                    <h2>电子病历撰写系统</h2>
                </div>
            </div>

            <div class="actions">
                <el-tooltip effect="dark" :content="useUserStore().shouldShow ? '收起侧边栏' : '展开侧边栏'" placement="bottom">
                    <span class="action-btn" @click="hiddenSidebar">
                        <el-icon :size="24">
                            <DArrowLeft v-if="useUserStore().shouldShow" />
                            <DArrowRight v-else />
                        </el-icon>
                    </span>
                </el-tooltip>
                
                <el-tooltip effect="dark" content="全屏" placement="bottom">
                    <span class="action-btn" @click="FullScreens">
                        <el-icon :size="20">
                            <FullScreen />
                        </el-icon>
                    </span>
                </el-tooltip>
                
                <el-tooltip effect="dark" content="简洁模式" placement="bottom">
                    <span class="action-btn" @click="FullScreens2">
                        <el-icon :size="20">
                            <Rank />
                        </el-icon>
                    </span>
                </el-tooltip>
            </div>
        </div>
        
        <div class="user-container">
            <div class="avatar-wrapper" @click="navigateToProfile">
                <el-tooltip effect="dark" content="个人信息" placement="bottom">
                    <div class="avatar">
                        <img :src="src" alt="User Avatar" />
                    </div>
                </el-tooltip>
                <span class="username">{{ userStore.$state.userInfo?.userName }}</span>
            </div>
            
            <el-tooltip effect="dark" content="退出登录" placement="bottom">
                <div class="logout-btn" @click="logout">
                    <svg t="1744190528338" class="icon" viewBox="0 0 1024 1024" version="1.1"
                        xmlns="http://www.w3.org/2000/svg" p-id="2635" width="20" height="20">
                        <path
                            d="M649.813333 808.533333L576 878.933333c-11.52 11.093333-26.88 17.066667-42.666667 17.066667H250.026667C206.08 896 170.666667 860.586667 170.666667 816.64V207.36C170.666667 163.413333 206.08 128 250.026667 128h281.6c16.64 0 32.426667 6.4 43.946666 18.346667l70.826667 70.826666a42.496 42.496 0 1 0 60.16-60.16L635.733333 85.76A146.56 146.56 0 0 0 531.626667 42.666667h-281.6C159.146667 42.666667 85.333333 116.48 85.333333 207.36v609.706667A164.693333 164.693333 0 0 0 250.026667 981.333333h283.306666c37.973333 0 74.24-14.506667 101.546667-40.533333l73.813333-69.973333c17.066667-16.213333 17.92-43.093333 1.706667-60.16a42.666667 42.666667 0 0 0-60.586667-2.133334z"
                            p-id="2636" fill="#ffffff"></path>
                        <path
                            d="M951.893333 481.706667l-143.786666-143.786667a42.496 42.496 0 1 0-60.16 60.16L818.773333 469.333333H412.586667c-23.466667 0-42.666667 19.2-42.666667 42.666667s19.2 42.666667 42.666667 42.666667h406.186666l-70.826666 70.826666a42.496 42.496 0 0 0 30.293333 72.533334c11.093333 0 21.76-4.266667 30.293333-12.373334l143.786667-143.786666c16.213333-16.213333 16.213333-43.52-0.426667-60.16z"
                            p-id="2637" fill="#ffffff"></path>
                    </svg>
                </div>
            </el-tooltip>
        </div>
    </div>
</template>

<style scoped>
.main-container {
    height: 60px;
    background: linear-gradient(135deg, #1e88e5 0%, #0d47a1 100%);
    color: white;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
    position: relative;
    z-index: 100;
}

.main-container::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 3px;
    background: linear-gradient(90deg, rgba(255,255,255,0.5) 0%, rgba(255,255,255,0.2) 100%);
    animation: shimmer 3s infinite linear;
}

@keyframes shimmer {
    0% { background-position: -200% 0; }
    100% { background-position: 200% 0; }
}

.logo-container {
    display: flex;
    align-items: center;
    gap: 20px;
}

.logo {
    display: flex;
    align-items: center;
    gap: 10px;
}

.title h2 {
    margin: 0;
    font-size: 18px;
    font-weight: 600;
    background: linear-gradient(to right, #ffffff, #e0f7fa);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.actions {
    display: flex;
    align-items: center;
    gap: 15px;
}

.action-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    cursor: pointer;
    transition: all 0.3s ease;
    color: white;
}

.action-btn:hover {
    background-color: rgba(255, 255, 255, 0.2);
    transform: scale(1.1);
}

.action-btn:active {
    transform: scale(0.95);
}

.user-container {
    display: flex;
    align-items: center;
    gap: 20px;
}

.avatar-wrapper {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    transition: all 0.3s ease;
}

.avatar-wrapper:hover {
    opacity: 0.8;
}

.avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    overflow: hidden;
    border: 2px solid rgba(255, 255, 255, 0.3);
    transition: all 0.3s ease;
}

.avatar:hover {
    border-color: white;
    transform: scale(1.05);
}

.avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.username {
    font-size: 14px;
    font-weight: 500;
}

.logout-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    cursor: pointer;
    transition: all 0.3s ease;
}

.logout-btn:hover {
    background-color: rgba(255, 255, 255, 0.2);
    transform: rotate(180deg);
}

.logout-btn:active {
    transform: scale(0.9) rotate(180deg);
}
</style>