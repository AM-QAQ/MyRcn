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
  <div class="settings-view">
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
        <div class="signin-info">
          <div class="info-item">
            <span class="label">上次签到时间:</span>
            <span class="value">2024-11-11 7:21:5</span>
          </div>
          <div class="info-item">
            <span class="label">连续签到天数:</span>
            <span class="value">1天</span>
          </div>
          <div class="info-item">
            <span class="label">Pro会员状态:</span>
            <span class="value">未解锁一个月Pro</span>
          </div>
        </div>
      </div>
      <div v-if="activeTab === '2'" class="tab-pane">
        <ul class="rules-list">
          <li>每日签到可获得奖励。</li>
          <li>连续签到14天，获得一个月Pro(一次性)。</li>
        </ul>
      </div>
      <div v-if="activeTab === '3'" class="tab-pane">
        <p>设置内容3</p>
      </div>
      <div v-if="activeTab === '4'" class="tab-pane">
        <p>设置内容4</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.settings-view {
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

.signin-info {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.info-item {
  display: flex;
  gap: 1rem;
}

.label {
  color: #888;
  min-width: 120px;
}

.value {
  color: #FFFFFF;
}

.rules-list {
  list-style: none;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.rules-list li {
  position: relative;
  padding-left: 1.5rem;
}

.rules-list li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: #636bfb;
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