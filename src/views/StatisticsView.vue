<script setup>
import { ref } from 'vue'

const activeTab = ref('签到')
const tabs = [
  { id: 'tab1', label: '签到' },
  { id: 'tab2', label: '规则' },
  { id: 'tab3', label: '使用统计' },
  { id: 'tab4', label: '其他数据' }
]
</script>

<template>
  <div class="statistics-view">
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
      <div v-if="activeTab === '签到'" class="tab-pane">
        <div class="stats-card signin-info">
          <div class="card-header">
            <h3>签到信息</h3>
          </div>
          <div class="card-content">
            <div class="info-item">
              <span class="label">上次签到时间:</span>
              <span class="value">2024-11-11 7:21:5</span>
            </div>
            <div class="info-item">
              <span class="label">连续签到天数:</span>
              <span class="value highlight">1天</span>
            </div>
            <div class="info-item">
              <span class="label">Pro会员状态:</span>
              <span class="value">未解锁一个月Pro</span>
            </div>
          </div>
        </div>
      </div>

      <div v-if="activeTab === '规则'" class="tab-pane">
        <div class="stats-card">
          <div class="card-header">
            <h3>签到规则</h3>
          </div>
          <div class="card-content">
            <ul class="rules-list">
              <li>每日签到可获得奖励</li>
              <li>连续签到14天，获得一个月Pro(一次性)</li>
              <li>断签会重置连续签到天数</li>
              <li>每月1号重置签到状态</li>
            </ul>
          </div>
        </div>
      </div>

      <div v-if="activeTab === '使用统计'" class="tab-pane">
        <div class="stats-card">
          <div class="card-header">
            <h3>使用数据</h3>
          </div>
          <div class="card-content">
            <div class="info-item">
              <span class="label">累计使用时长:</span>
              <span class="value highlight">72小时</span>
            </div>
            <div class="info-item">
              <span class="label">本月活跃天数:</span>
              <span class="value">15天</span>
            </div>
            <div class="info-item">
              <span class="label">最常用功能:</span>
              <span class="value">快速绑定</span>
            </div>
          </div>
        </div>
      </div>

      <div v-if="activeTab === '其他数据'" class="tab-pane">
        <div class="stats-card">
          <div class="card-header">
            <h3>其他统计</h3>
          </div>
          <div class="card-content">
            <div class="info-item">
              <span class="label">账号注册时间:</span>
              <span class="value">2024-01-01</span>
            </div>
            <div class="info-item">
              <span class="label">最近登录时间:</span>
              <span class="value">2024-01-15</span>
            </div>
            <div class="info-item">
              <span class="label">设备绑定数:</span>
              <span class="value">1台</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.statistics-view {
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
  scrollbar-width: none;
  -ms-overflow-style: none;
}

.tabs::-webkit-scrollbar {
  display: none;
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

.stats-card {
  background: linear-gradient(145deg, rgba(99, 107, 251, 0.05), rgba(99, 107, 251, 0.02));
  border-radius: 12px;
  border: 1px solid rgba(99, 107, 251, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.stats-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.card-header {
  padding: 1rem 1.5rem;
  border-bottom: 1px solid rgba(99, 107, 251, 0.1);
}

.card-header h3 {
  margin: 0;
  color: #636bfb;
  font-size: 1.25rem;
  font-weight: 500;
}

.card-content {
  padding: 1.5rem;
}

.info-item {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.info-item:last-child {
  margin-bottom: 0;
}

.label {
  color: #888;
  min-width: 120px;
}

.value {
  color: #FFFFFF;
}

.value.highlight {
  color: #636bfb;
  font-weight: 500;
}

.rules-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.rules-list li {
  position: relative;
  padding-left: 1.5rem;
  color: #FFFFFF;
}

.rules-list li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: #636bfb;
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

  .card-header {
    padding: 1rem;
  }

  .card-content {
    padding: 1rem;
  }

  .info-item {
    flex-direction: column;
    gap: 0.5rem;
  }

  .label {
    min-width: auto;
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