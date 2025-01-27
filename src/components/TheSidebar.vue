<script setup>
import { ref } from 'vue'

const isCollapsed = ref(false)
const emit = defineEmits(['toggle-sidebar'])

const toggleSidebar = () => {
  isCollapsed.value = !isCollapsed.value
  emit('toggle-sidebar', isCollapsed.value)
}

// 侧边栏选项
const menuItems = [
  { icon: '🚀', label: 'Pro教程', route: '/pro' },
  { icon: '🎮', label: '游戏教程', route: '/game' },
  { icon: '⬇️', label: '游戏下载', route: '/download' },
  { icon: '⚙️', label: '系统设置', route: '/settings' }
]
</script>

<template>
  <div class="sidebar-container">
    <div 
      v-show="!isCollapsed" 
      class="sidebar-overlay"
      @click="toggleSidebar"
    ></div>
    <aside :class="['sidebar', { 'collapsed': isCollapsed }]">
      <div class="sidebar-header">
        <a 
          href="https://github.com/AM-QAQ/MyRcn" 
          target="_blank" 
          class="logo" 
          v-show="!isCollapsed"
        >
          <img src="@/assets/img/AMt.ico" alt="Logo" class="logo-img">
          <span class="logo-text">MyRcn</span>
        </a>
        <button class="toggle-btn" @click="toggleSidebar">
          <span class="toggle-icon">{{ isCollapsed ? '☰' : '×' }}</span>
        </button>
      </div>
      
      <nav class="menu">
        <router-link
          v-for="item in menuItems"
          :key="item.route"
          :to="item.route"
          class="menu-item"
          active-class="active"
          exact
        >
          <span class="icon">{{ item.icon }}</span>
          <span class="label" v-show="!isCollapsed">{{ item.label }}</span>
        </router-link>
      </nav>
    </aside>

    <!-- 移动端固定展开按钮 -->
    <button 
      v-show="isCollapsed" 
      class="mobile-toggle-btn"
      @click="toggleSidebar"
    >
      <span class="toggle-icon">☰</span>
    </button>
  </div>
</template>

<style scoped>
.sidebar-container {
  position: relative;
  z-index: 100;
}

.sidebar-overlay {
  display: none;
}

.mobile-toggle-btn {
  display: none;
}

.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  height: 100vh;
  background-color: #13131a;
  transition: all 0.3s ease;
  width: 240px;
  display: flex;
  flex-direction: column;
}

.sidebar.collapsed {
  width: 72px;
}

.sidebar-header {
  height: 60px;
  display: flex;
  align-items: center;
  padding: 0 1rem;
  position: relative;
}

.sidebar-header::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 1rem;
  right: 1rem;
  height: 2px;
  background-color: #2f2f3d;
  opacity: 1;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-weight: bold;
  color: #636bfb;
  transition: all 0.3s ease;
  padding: 0.5rem;
  border-radius: 4px;
  text-decoration: none;
  flex: 1;
}

.logo:hover {
  background-color: rgba(99, 107, 251, 0.05);
}

.logo:hover .logo-img {
  transform: rotate(360deg);
}

.logo-img {
  width: 28px;
  height: 28px;
  transition: transform 0.6s ease;
}

.logo-text {
  font-size: 1.2rem;
  letter-spacing: 0.5px;
}

.toggle-btn {
  width: 32px;
  height: 32px;
  background: transparent;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #FFFFFF;
  transition: all 0.2s ease;
}

/* 当侧边栏收起时的按钮样式 */
.sidebar.collapsed .sidebar-header {
  justify-content: center;
}

.sidebar.collapsed .toggle-btn {
  margin: 0;
}

.toggle-btn:hover {
  background-color: rgba(99, 107, 251, 0.05);
  border-radius: 4px;
  transform: scale(1.1);
}

.toggle-btn:active {
  transform: scale(0.95);
}

.toggle-icon {
  font-size: 20px;
  line-height: 1;
}

.menu {
  flex: 1;
  padding: 1rem 0;
  overflow-y: auto;
}

.menu-item {
  display: flex;
  align-items: center;
  padding: 0.75rem 1rem;
  color: #FFFFFF;
  text-decoration: none;
  transition: all 0.3s ease;
  gap: 0.75rem;
  position: relative;
  overflow: hidden;
  margin: 0 0.5rem;
  border-radius: 6px;
}

.menu-item::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 0;
  background-color: rgba(255, 255, 255, 0.1);
  z-index: -1;
  transition: width 0.3s ease;
  border-radius: 6px;
}

.menu-item:hover::before {
  width: 100%;
  background-color: rgba(99, 107, 251, 0.05);
}

.menu-item:hover .icon {
  transform: scale(1.2);
}

.menu-item:active {
  transform: translateX(4px);
}

.menu-item.active {
  background-color: transparent;
  font-weight: 500;
  position: relative;
  border-radius: 6px;
  margin: 0 0.5rem;
  color: #646cff;
}

.menu-item.active::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 3px;
  background-color: #646CFF;
  z-index: -1;
}

.menu-item.active::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: rgba(100, 108, 255, 0.1);
  z-index: -2;
  border-radius: 6px;
}

.icon {
  font-size: 1.2rem;
  width: 24px;
  text-align: center;
  transition: transform 0.2s ease;
}

.label {
  white-space: nowrap;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .sidebar-overlay {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 90;
  }

  .mobile-toggle-btn {
    display: flex;
    position: fixed;
    left: 0.5rem;
    top: 1rem;
    width: 40px;
    height: 40px;
    background-color: #0a0a0f;
    border: none;
    border-radius: 4px;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    z-index: 80;
    color: #FFFFFF;
    transition: all 0.2s ease;
  }

  .mobile-toggle-btn:hover {
    background-color: rgba(99, 107, 251, 0.05);
    transform: scale(1.1);
  }

  .mobile-toggle-btn:active {
    transform: scale(0.95);
  }

  .sidebar {
    z-index: 100;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
  }

  .sidebar.collapsed {
    transform: translateX(-100%);
    width: 240px;
  }

  .sidebar-overlay {
    opacity: 0;
    transition: opacity 0.3s ease;
  }

  .sidebar-overlay:not([v-show="false"]) {
    opacity: 1;
  }

  /* 确保展开时logo始终显示 */
  .logo {
    display: flex !important;
  }
}

/* 滚动条样式 */
.menu::-webkit-scrollbar {
  width: 4px;
}

.menu::-webkit-scrollbar-track {
  background: transparent;
}

.menu::-webkit-scrollbar-thumb {
  background-color: var(--color-border);
  border-radius: 2px;
}

.menu::-webkit-scrollbar-thumb:hover {
  background-color: var(--color-text);
}
</style> 