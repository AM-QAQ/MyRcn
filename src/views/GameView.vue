<script setup>
import { ref } from 'vue'

const activeTab = ref('购买')
const tabs = [
  { id: 'tab1', label: '购买' },
  { id: 'tab2', label: '使用' },
  { id: 'tab3', label: '反馈' },
  { id: 'tab4', label: '问题' }
]
</script>

<template>
  <div class="game-view">
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
      <div v-if="activeTab === '购买'" class="tab-pane">
        <p>游戏教程内容1</p>
      </div>
      <div v-if="activeTab === '使用'" class="tab-pane">
        <p>游戏教程内容2</p>
      </div>
      <div v-if="activeTab === '反馈'" class="tab-pane">
        <p>游戏教程内容3</p>
      </div>
      <div v-if="activeTab === '问题'" class="tab-pane">
        <p>游戏教程内容4</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.game-view {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.tabs {
  display: flex;
  gap: 1rem;
  border-bottom: 2px solid #2f2f3d;
  padding-bottom: 0.5rem;
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none; /* Firefox */
  -ms-overflow-style: none; /* IE and Edge */
}

.tabs::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera */
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
  white-space: nowrap;
  min-width: max-content;
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

/* 移动端适配 */
@media (max-width: 768px) {
  .tabs {
    gap: 0.5rem;
    padding: 0.5rem;
    margin: 0 -0.5rem;
  }

  .tab-btn {
    padding: 0.5rem 0.75rem;
    font-size: 0.9rem;
  }
}

/* 超小屏幕适配 */
@media (max-width: 360px) {
  .tabs {
    gap: 0.25rem;
  }

  .tab-btn {
    padding: 0.5rem;
  }
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