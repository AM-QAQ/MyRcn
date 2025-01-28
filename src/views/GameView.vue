<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import "@/assets/styles/views.css"

const activeTab = ref('开房间')
const showBackTop = ref(false)

const tabs = [
  { id: 'tab1', label: '开房间' },
  { id: 'tab2', label: '指令' },
  { id: 'tab3', label: '问题' },
  { id: 'tab4', label: '反馈' }
]

const handleScroll = () => {
  showBackTop.value = window.scrollY > 300
}

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <div class="pro-view">
    <div class="tabs">
      <button v-for="tab in tabs" :key="tab.id" :class="['tab-btn', { active: activeTab === tab.label }]"
        @click="activeTab = tab.label">
        {{ tab.label }}
      </button>
    </div>

    <div class="tab-content">
      <div v-if="activeTab === '开房间'" class="tab-pane">
        <div class="purchase-guide">
          <div class="step-card">
            <div class="step-header">
              <div class="step-number">01</div>
              <div class="step-title">输入一个不存在的房间号<span class="highlight">RXXXXX</span>，并加入</div>
            </div>
            <div class="step-content">
              <div class="img-container">
                <img src="@/assets/img/game/输入房间号.png" alt="buying-加载失败">
              </div>
            </div>
          </div>

          <div class="step-card">
            <div class="step-header">
              <div class="step-number">02</div>
              <div class="step-title">
                在弹出窗口中输入
                <span class="highlight">newup</span>，
                并点击
                <span class="highlight">Submit</span>
              </div>
            </div>
            <div class="step-content">
              <div class="img-container">
                <img src="@/assets/img/game/输入开房指令.png" alt="buying-加载失败">
                <div class="warning-text">指令补充：</div>
                <div class="img-container">
                  <img src="@/assets/img/game/开房指令.png" alt="buying-加载失败">
                </div>
              </div>
            </div>
          </div>

          <div class="step-card">
            <div class="step-header">
              <div class="step-number">03</div>
              <div class="step-title">在聊天栏可查看房间公开状态</div>
            </div>
            <div class="step-content">
              <div class="img-container">
                <li>成功：</li>
                <img src="@/assets/img/game/公开成功.png" alt="buying-加载失败">
                <br><br>
                <li>失败：</li>
                <img src="@/assets/img/game/公开失败.png" alt="buying-加载失败">
              </div>
            </div>
          </div>

          <div class="usage-note">
            <div class="note-icon">📝</div>
            <p>
              公开失败代表外面房间已满，可让玩家直接输入<span class="highlight">RXXXXX</span>加入房间。
              也可在聊天框发送<span class="highlight">.toup</span>尝试再次公开。
            </p>
          </div>
        </div>
      </div>

      <div v-if="activeTab === '指令'" class="tab-pane">
        <div class="usage-guide">
          <div class="method-card">
            <div class="method-header">
              <div class="method-title">
                <span class="method-badge">原版</span>
              </div>
            </div>
            <div class="method-content">
              <div class="usage-step">
                <div class="step-text">
                  <div class="command-list">
                    <div class="command-item">
                      <span class="command">.id</span>
                      <span class="description">查看房间号</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.toup</span>
                      <span class="description">公开房间</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.tonp</span>
                      <span class="description">取消公开</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.set am on</span>
                      <span class="description">设置房间混战</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.self_move [n]</span>
                      <span class="description">设置自己位置</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.self_team [n]</span>
                      <span class="description">设置自己队伍</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.set team [n]</span>
                      <span class="description">设置房间总队伍数</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.allmute</span>
                      <span class="description">全体禁言</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.sync [on/off]</span>
                      <span class="description">设置是否启用房间重连</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.kick [n]</span>
                      <span class="description">踢出玩家</span>
                    </div>
                    <div class="command-item waiting">
                      <span class="description">更多指令待补充...</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="method-card">
            <div class="method-header">
              <div class="method-title">
                <span class="method-badge">指令版</span>
              </div>
            </div>
            <div class="method-content">
              <div class="usage-step">
                <div class="step-text">
                  <div class="command-list">
                    <div class="command-item">
                      <span class="command">.income [n]</span>
                      <span class="description">设置房间倍数</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.setmaxteamid [n]</span>
                      <span class="description">设置房间最大人数</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.op [n]</span>
                      <span class="description">给予房主权限</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.unop [n]</span>
                      <span class="description">取消房主权限</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.nukes [on/off]</span>
                      <span class="description">设置是否开启核弹</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.mute [n]</span>
                      <span class="description">禁言玩家</span>
                    </div>
                    <div class="command-item">
                      <span class="command">.unmute [n]</span>
                      <span class="description">解除禁言</span>
                    </div>
                    <div class="command-item waiting">
                      <span class="description">更多指令待补充...</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div v-if="activeTab === '问题'" class="tab-pane">
        <div class="faq-container">
          <div class="faq-item">
            <div class="faq-question">
              <span class="question-number">Q1</span>
              <span class="question-text">
                1
              </span>
            </div>
            <div class="faq-answer">
              1
            </div>
          </div>

          <div class="faq-item">
            <div class="faq-question">
              <span class="question-number">Q2</span>
              <span class="question-text">2</span>
            </div>
            <div class="faq-answer">
              2
            </div>
          </div>

          <div class="faq-item">
            <div class="faq-question">
              <span class="question-number">Q3</span>
              <span class="question-text">待补充</span>
            </div>
            <div class="faq-answer">
              敬请期待...
            </div>
          </div>
        </div>
      </div>
      <div v-if="activeTab === '反馈'" class="tab-pane">
        <div class="feedback-container">
          <div class="feedback-card">
            <div class="group-info">
              <div class="group-title">RELAY-CN交流群</div>
              <a href="https://qm.qq.com/q/ncj4vfZ3OM"
                target="_blank" 
                class="group-number"
                title="点击加入群聊"
              >
                885925961
              </a>
            </div>
          </div>

          <div class="feedback-card">
            <div class="group-info">
              <div class="group-title">邮箱反馈</div>
              <a href="mailto:IronCore@der.kim?subject=游戏反馈&body=请在此处输入您的反馈内容..."
                target="_blank" 
                class="group-number"
                title="点击发送邮件"
              >
                IronCore@der.kim
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- 返回顶部按钮 -->
    <button v-show="showBackTop" class="back-to-top" @click="scrollToTop" title="返回顶部">
      ↑
    </button>
  </div>
</template>

<!-- 指令展示样式 -->
<style scoped>
.command-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.command-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 0.5rem;
  border-radius: 6px;
  background-color: rgba(99, 107, 251, 0.05);
  transition: all 0.3s ease;
}

.command-item:hover {
  background-color: rgba(99, 107, 251, 0.1);
  transform: translateX(4px);
}

.command {
  color: var(--accent-color);
  font-family: monospace;
  font-size: 1rem;
  font-weight: 500;
  min-width: 140px;
}

.description {
  color: var(--text-primary);
}

.waiting {
  color: var(--text-secondary);
  font-style: italic;
  justify-content: center;
}

/* 移动端适配 */
@media (max-width: 768px) {
  .command-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }

  .command {
    min-width: auto;
  }
}
</style>