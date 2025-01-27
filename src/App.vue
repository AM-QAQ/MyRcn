<script setup>
import { RouterView, useRoute } from 'vue-router'
import { computed, ref, watch } from 'vue'
import TheSidebar from './components/TheSidebar.vue'

const route = useRoute()
const isCollapsed = ref(false)

const currentTitle = computed(() => {
  const titles = {
    '/pro': 'Pro教程',
    '/game': '游戏教程',
    '/download': '游戏下载',
    '/settings': '系统设置'
  }
  return titles[route.path] || ''
})

// 处理侧边栏状态变化
const handleSidebarToggle = (collapsed) => {
  isCollapsed.value = collapsed
}
</script>

<template>
  <div class="app-container">
    <TheSidebar @toggle-sidebar="handleSidebarToggle"/>
    <div :class="['main-wrapper', { 'collapsed': isCollapsed }]">
      <header class="title-bar">
        <h1 class="page-title">{{ currentTitle }}</h1>
      </header>
      <main class="main-content">
        <div class="content-container">
          <RouterView />
        </div>
      </main>
    </div>
  </div>
</template>

<style>
.app-container {
  min-height: 100vh;
  display: flex;
  background-color: #0a0a0f;
}

.main-wrapper {
  flex: 1;
  margin-left: 240px;
  transition: all 0.3s ease;
}

.main-wrapper.collapsed {
  margin-left: 72px;
}

/* 标题栏 */
.title-bar {
  height: 60px;
  background-color: #13131a;
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  left: 240px;
  right: 0;
  top: 0;
  z-index: 50;
  transition: all 0.3s ease;
}

.main-wrapper.collapsed .title-bar {
  left: 72px;
}

.page-title {
  font-size: 1.5rem;
  font-weight: 500;
  color: #636bfb;
  margin: 0;
}

.main-content {
  padding: 2rem;
  padding-top: calc(60px + 2rem);
  display: flex;
  justify-content: center;
}

.content-container {
  background-color: #13131a;
  border-radius: 12px;
  padding: 2rem;
  min-height: calc(100vh - 60px - 4rem);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
  width: 100%;
  max-width: 800px;
  color: #FFFFFF;
  border: 1px solid #1f1f2b;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .main-wrapper {
    margin-left: 0;
  }

  .main-wrapper.collapsed {
    margin-left: 0;
  }

  .title-bar {
    left: 0;
    padding: 0 3rem;
  }

  .main-wrapper.collapsed .title-bar {
    left: 0;
  }

  .main-content {
    padding: 1rem;
    padding-top: calc(60px + 1rem);
  }

  .content-container {
    padding: 1.5rem;
    min-height: calc(100vh - 60px - 2rem);
    max-width: 100%;
  }

  .mobile-toggle-btn {
    background-color: #13131a;
  }
}
</style>
