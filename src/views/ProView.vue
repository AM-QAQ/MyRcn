<script setup>
import { ref } from 'vue'

const activeTab = ref('购买')
const tabs = [
    { id: 'tab1', label: '购买' },
    { id: 'tab2', label: '使用' },
    { id: 'tab3', label: '问题' },
    { id: 'tab4', label: '反馈' }
]
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
            <div v-if="activeTab === '购买'" class="tab-pane">
                <div class="purchase-guide">
                    <div class="step-card">
                        <div class="step-header">
                            <div class="step-number">01</div>
                            <div class="step-title">访问服务网站</div>
                        </div>
                        <div class="step-content">
                            <p>在浏览器输入 <a href="https://service.rw.der.kim" target="_blank" class="highlight-link">service.rw.der.kim</a></p>
                            <div class="img-container">
                                <img src="@/assets/img/pro/buying-1.png" alt="buying-加载失败">
                            </div>
                        </div>
                    </div>

                    <div class="step-card">
                        <div class="step-header">
                            <div class="step-number">02</div>
                            <div class="step-title">注册账号</div>
                        </div>
                        <div class="step-content">
                            <p>点击<span class="highlight">立即开始</span>或<span class="highlight">登录</span>，进入登录界面<span class="highlight">注册账号</span></p>
                            <div class="warning-text">请牢记您的账号密码，这很重要</div>
                            <div class="img-container">
                                <img src="@/assets/img/pro/buying-2.png" alt="buying-加载失败">
                            </div>
                        </div>
                    </div>

                    <div class="step-card">
                        <div class="step-header">
                            <div class="step-number">03</div>
                            <div class="step-title">充值服务</div>
                        </div>
                        <div class="step-content">
                            <p>在左侧菜单栏选择<span class="highlight">服务->钱包->自助充值</span>，根据需要购买的套餐充值对应的金额<span class="highlight">(6/月)</span></p>
                            <div class="img-container">
                                <img src="@/assets/img/pro/buying-8.png" alt="buying-加载失败">
                            </div>
                        </div>
                    </div>

                    <div class="step-card">
                        <div class="step-header">
                            <div class="step-number">04</div>
                            <div class="step-title">完成支付</div>
                        </div>
                        <div class="step-content">
                            <p>保存支付的二维码在微信完成支付</p>
                            <div class="warning-text">若微信不支持图片扫码支付，可使用手机扫码电脑上的二维码</div>
                            <p>充值完成后选择<span class="highlight">服务->购买服务</span>，购买需要的套餐</p>
                            <div class="img-container">
                                <img src="@/assets/img/pro/buying-9.png" alt="buying-加载失败">
                            </div>
                        </div>
                    </div>

                    <div class="step-card">
                        <div class="step-header">
                            <div class="step-number">05</div>
                            <div class="step-title">查看到期时间</div>
                        </div>
                        <div class="step-content">
                            <p>购买成功后可在<span class="highlight">RCN-Pro -> 设置</span>中查看到期时间</p>
                            <div class="img-container">
                                <img src="@/assets/img/pro/buying-10.png" alt="buying-加载失败">
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div v-if="activeTab === '使用'" class="tab-pane">
                <div class="usage-guide">
                    <div class="method-card">
                        <div class="method-header">
                            <div class="method-title">
                                <span class="method-badge">方法一</span>
                                <span>快速绑定</span>
                            </div>
                        </div>
                        <div class="method-content">
                            <div class="usage-step">
                                <div class="step-text">
                                    <span class="step-marker">1</span>
                                    <p>在左侧菜单选择<span class="highlight">RCN-Pro->绑定</span>，确定"快速绑定/慢速绑定修改"为<span class="highlight">启用</span></p>
                                    <div class="warning-text">默认就是启用状态</div>
                                    <p>以防万一，手动更新一下IP</p>
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-1.png" alt="使用说明图片">
                                </div>
                            </div>

                            <div class="usage-step">
                                <div class="step-text">
                                    <span class="step-marker">2</span>
                                    <p>登录游戏，在IP地址栏输入<span class="highlight">sssss</span></p>
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-2.png" alt="图片加载失败">
                                </div>
                            </div>

                            <div class="usage-step">
                                <div class="step-text">
                                    <span class="step-marker">3</span>
                                    <p>在弹出的提示框中输入<span class="highlight">newup</span>，注意查看房间提示确定是否公开</p>
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-3.png" alt="图片加载失败">
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-4.png" alt="图片加载失败">
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="method-card">
                        <div class="method-header">
                            <div class="method-title">
                                <span class="method-badge">方法二</span>
                                <span>慢速绑定</span>
                                <span class="recommend-badge">推荐</span>
                            </div>
                        </div>
                        <div class="method-content">
                            <div class="usage-step">
                                <div class="step-text">
                                    <span class="step-marker">1</span>
                                    <p>在左侧菜单选择<span class="highlight">RCN-Pro->绑定</span>，确定"快速绑定/慢速绑定修改"为<span class="highlight">禁用</span></p>
                                    <p>并复制下方<span class="highlight">慢速绑定码</span></p>
                                    <div class="warning-text">注意不要向他人暴露您的慢速绑定码</div>
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-5.png" alt="图片加载失败">
                                </div>
                            </div>

                            <div class="usage-step">
                                <div class="step-text">
                                    <span class="step-marker">2</span>
                                    <p>登录游戏在IP地址栏输入<span class="highlight">sssss</span></p>
                                    <p>在弹窗中输入所复制的<span class="highlight">慢速绑定码</span></p>
                                    <p>显示绑定成功后再输入<span class="highlight">newup</span></p>
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-2.png" alt="图片加载失败">
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-6.png" alt="图片加载失败">
                                </div>
                                <div class="img-container">
                                    <img src="@/assets/img/pro/use-7.png" alt="图片加载失败">
                                </div>
                            </div>

                            <div class="usage-note">
                                <div class="note-icon">📝</div>
                                <p>慢速绑定最多绑定两个设备，若需要绑定新的设备请在<span class="highlight">RCN-Pro->绑定</span>删除无用的设备</p>
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
                            <span class="question-text">我已经购买了Pro为什么开房间还是显示无权使用？</span>
                        </div>
                        <div class="faq-answer">
                            请试着在当前游戏设备上重新登录Pro网站或更换网络
                        </div>
                    </div>

                    <div class="faq-item">
                        <div class="faq-question">
                            <span class="question-number">Q2</span>
                            <span class="question-text">我在使用S房时闪退情况频发，且有时候创建房间会卡住</span>
                        </div>
                        <div class="faq-answer">
                            可能是当前使用的服务器出现了问题，请根据下图更改节点：
                            <div class="img-container">
                                <img src="@/assets/img/pro/节点修改.png" alt="图片加载失败">
                            </div>
                        </div>
                    </div>

                    <div class="faq-item">
                        <div class="faq-question">
                            <span class="question-number">Q3</span>
                            <span class="question-text">我在使用慢速绑定时出现了"绑定码无法对应IP"的错误</span>
                        </div>
                        <div class="faq-answer">
                            <div class="img-container">
                                <img src="@/assets/img/pro/慢绑错误2.png" alt="图片加载失败">
                            </div>
                            请试着在当前游戏设备上登录Pro网站后再进行慢速绑定
                        </div>
                    </div>

                    <div class="faq-item">
                        <div class="faq-question">
                            <span class="question-number">Q4</span>
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
                            <a href="https://qm.qq.com/cgi-bin/qm/qr?k=YvFmSPDhRGBGVgEbZXFxVtHLGxvZZxeL&jump_from=webapi&authKey=Hs0XSXw+kRH6/+YHEkZQvJXBxVhkxZRQFLuQvbmEo+Ry+6QvHJPNBUQaGXKv5Vqj" target="_blank" class="group-number">
                                885925961
                            </a>
                        </div>
                    </div>
                    
                    <div class="feedback-card">
                        <div class="group-info">
                            <div class="group-title">Pro交流群</div>
                            <a href="https://qm.qq.com/cgi-bin/qm/qr?k=YvFmSPDhRGBGVgEbZXFxVtHLGxvZZxeL&jump_from=webapi&authKey=Hs0XSXw+kRH6/+YHEkZQvJXBxVhkxZRQFLuQvbmEo+Ry+6QvHJPNBUQaGXKv5Vqj" target="_blank" class="group-number">
                                414204970
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.pro-view {
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

.img-container {
    max-width: 100%;
    /* 容器最大宽度为100% */
    text-align: left;
    /* buying-居中显示 */
    margin: 20px 0;
    /* buying-上下留白 */
}

.img-container img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
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

/* FAQ样式 */
.faq-container {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

.faq-item {
    background-color: rgba(99, 107, 251, 0.05);
    border-radius: 8px;
    padding: 1.5rem;
    border: 1px solid rgba(99, 107, 251, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.faq-item:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.faq-question {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    margin-bottom: 1rem;
    color: #636bfb;
    font-weight: 500;
}

.question-number {
    background-color: #636bfb;
    color: white;
    padding: 0.25rem 0.5rem;
    border-radius: 4px;
    font-size: 0.9rem;
}

.question-text {
    font-size: 1.1rem;
    line-height: 1.5;
}

.faq-answer {
    color: #FFFFFF;
    line-height: 1.6;
    padding-left: calc(2rem + 1.5rem);
}

.faq-answer .img-container {
    margin: 1rem 0;
}

/* 购买部分样式 */
.purchase-guide {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

.step-card {
    background: linear-gradient(145deg, rgba(99, 107, 251, 0.05), rgba(99, 107, 251, 0.02));
    border-radius: 12px;
    padding: 1.5rem;
    border: 1px solid rgba(99, 107, 251, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.step-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.step-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.5rem;
}

.step-number {
    font-size: 1.5rem;
    font-weight: bold;
    color: #636bfb;
    background: rgba(99, 107, 251, 0.1);
    padding: 0.5rem 1rem;
    border-radius: 8px;
}

.step-title {
    font-size: 1.25rem;
    font-weight: 500;
    color: #FFFFFF;
}

.step-content {
    color: #FFFFFF;
    line-height: 1.6;
}

.highlight {
    color: #636bfb;
    font-weight: 500;
}

.highlight-link {
    color: #636bfb;
    text-decoration: none;
    font-weight: 500;
    transition: color 0.3s ease;
}

.highlight-link:hover {
    color: #8389ff;
}

.warning-text {
    color: #ff6b6b;
    margin: 0.5rem 0;
    font-style: italic;
}

/* 使用部分样式 */
.usage-guide {
    display: flex;
    flex-direction: column;
    gap: 3rem;
}

.method-card {
    background: linear-gradient(145deg, rgba(99, 107, 251, 0.05), rgba(99, 107, 251, 0.02));
    border-radius: 12px;
    padding: 2rem;
    border: 1px solid rgba(99, 107, 251, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.method-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.method-header {
    margin-bottom: 2rem;
}

.method-title {
    display: flex;
    align-items: center;
    gap: 1rem;
    font-size: 1.25rem;
    color: #FFFFFF;
}

.method-badge {
    background: #636bfb;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 6px;
    font-size: 1rem;
    font-weight: 500;
}

.recommend-badge {
    background: #ff6b6b;
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 4px;
    font-size: 0.9rem;
}

.method-content {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}

.usage-step {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.step-text {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    position: relative;
    padding-left: 2.5rem;
    color: #FFFFFF;
}

.step-marker {
    position: absolute;
    left: 0;
    background: rgba(99, 107, 251, 0.1);
    color: #636bfb;
    width: 1.75rem;
    height: 1.75rem;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-weight: bold;
}

.usage-note {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    background: rgba(255, 255, 255, 0.05);
    padding: 1rem;
    border-radius: 8px;
    margin-top: 1rem;
    color: #FFFFFF;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.usage-note:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.note-icon {
    font-size: 1.25rem;
}

/* 反馈部分样式 */
.feedback-container {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    max-width: 600px;
    margin: 0 auto;
}

.feedback-card {
    background: linear-gradient(145deg, rgba(99, 107, 251, 0.05), rgba(99, 107, 251, 0.02));
    border-radius: 12px;
    padding: 2rem;
    border: 1px solid rgba(99, 107, 251, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.feedback-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}

.group-info {
    text-align: center;
    color: #FFFFFF;
}

.group-title {
    font-size: 1.25rem;
    font-weight: 500;
    margin-bottom: 1rem;
    color: #636bfb;
}

.group-number {
    font-size: 1.5rem;
    font-weight: bold;
    background: rgba(99, 107, 251, 0.1);
    padding: 1rem;
    border-radius: 8px;
    color: #FFFFFF;
    text-decoration: none;
    display: block;
    transition: all 0.3s ease;
}

.group-number:hover {
    background: rgba(99, 107, 251, 0.2);
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(99, 107, 251, 0.1);
}
</style>