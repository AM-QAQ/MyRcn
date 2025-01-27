<script setup>
import { ref } from 'vue'

const activeTab = ref('1')
const tabs = [
  { id: 'tab1', label: '1' },
  { id: 'tab2', label: '2' },
  { id: 'tab3', label: '3' },
  { id: 'tab4', label: '4' }
]
</script>

<template>
  <div class="download-view">
    <div class="tabs">
      <button 
        v-for="tab in tabs" 
        :key="tab.id"
        :class="['tab-btn', { active: activeTab === tab.label }]"
        @click="activeTab = tab.label"
      >
        {{ tab.label }}
      </button>
    </div>

    <div class="tab-content">
      <div v-if="activeTab === '1'" class="tab-pane">
        <p>游戏下载内容1</p>
      </div>
      <div v-if="activeTab === '2'" class="tab-pane">
        <p>游戏下载内容2</p>
      </div>
      <div v-if="activeTab === '3'" class="tab-pane">
        <p>游戏下载内容3</p>
      </div>
      <div v-if="activeTab === '4'" class="tab-pane">
        <p>游戏下载内容4</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.download-view {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.tabs {
  display: flex;
  gap: 1rem;
  border-bottom: 2px solid #2f2f3d;
  padding-bottom: 0.5rem;
}

.tab-btn {
  background: none;
  border: none;
  color: #FFFFFF;
  font-size: 1rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
}

.tab-btn::after {
  content: '';
  position: absolute;
  bottom: -0.5rem;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #636bfb;
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

.tab-btn.active {
  color: #636bfb;
}

.tab-btn.active::after {
  transform: scaleX(1);
}

.tab-content {
  padding: 1rem 0;
}

.tab-pane {
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style> 