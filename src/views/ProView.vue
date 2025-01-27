<script setup>
import { ref } from 'vue'

const activeTab = ref('购买')
const tabs = [
    { id: 'tab1', label: '购买' },
    { id: 'tab2', label: '使用' },
    { id: 'tab3', label: '常见问题' },
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

                <p>1.在浏览器输入<a href="https://service.rw.der.kim" target="_blank"
                        style="color: chocolate;">service.rw.der.kim</a></p>
                <div class="img-container">
                    <img src="@/assets/img/pro/buying-1.png" alt="buying-加载失败">
                </div>

                <p>
                    2.点击<b style="color:chocolate;">立即开始</b>
                    或<b style="color:chocolate;">登录</b>，
                    进入登录界面<b style="color:chocolate;">注册账号</b></p>
                <i style="color:red;">请牢记您的账号密码，这很重要</i>

                <div class="img-container">
                    <img src="@/assets/img/pro/buying-2.png" alt="buying-加载失败">
                </div>

                <p>
                    3.在左侧菜单栏选择<b style="color:chocolate;">服务->钱包->自助充值</b>，
                    根据需要购买的套餐充值对应的金额<b style="color:chocolate;">(6/月)</b>
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/buying-8.png" alt="buying-加载失败">
                </div>

                <p>
                    4.保存支付的二维码在微信完成支付<br>
                <p style="color:red;">（若微信不支持图片扫码支付，可使用手机扫码电脑上的二维码）</p>
                充值完成后选择<b style="color:chocolate;">服务->购买服务</b>，
                购买需要的套餐
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/buying-9.png" alt="buying-加载失败">
                </div>

                <p>
                    5.购买成功后可在<b style="color:chocolate;">RCN-Pro -> 设置</b>
                    中查看到期时间
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/buying-10.png" alt="buying-加载失败">
                </div>
            </div>
            <div v-if="activeTab === '使用'" class="tab-pane">

                <p><i>★方法一（快速绑定）</i></p>

                <p>
                    1.在左侧菜单选择<b style="color:chocolate;">RCN-Pro->绑定</b>，
                    确定“快速绑定/慢速绑定修改”为<b style="color:chocolate;">启用</b><br>
                    <i style="color: red;">（默认就是启用状态）</i><br>
                    以防万一，手动更新一下IP
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-1.png" alt="使用说明图片">
                </div>

                <p>
                    2.登录游戏，在IP地址栏输入<b style="color:chocolate;">sssss</b>
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-2.png" alt="图片加载失败">
                </div>

                <p>
                    3.在弹出的提示框中输入<b style="color:chocolate;">newup</b>，注意查看房间提示确定是否公开
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-3.png" alt="图片加载失败">
                </div>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-4.png" alt="图片加载失败">
                </div>


                <p><i>★方法二（慢速绑定）</i><span style="color: red;"> 推荐</span></p>

                <p>
                    1.在左侧菜单选择<b style="color:chocolate;">RCN-Pro->绑定</b>，
                    确定“快速绑定/慢速绑定修改”为<b style="color:chocolate;">禁用</b><br>
                    并复制下方<b style="color:chocolate;">慢速绑定码</b><br>
                    <i style="color:red;">注意不要向他人暴露您的慢速绑定码</i>
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-5.png" alt="图片加载失败">
                </div>

                <p>
                    2.登录游戏在IP地址栏输入<b style="color:chocolate;">sssss</b> <br>
                    在弹窗中输入所复制的<b style="color:chocolate;">慢速绑定码</b><br>
                    显示绑定成功后再输入<b style="color:chocolate;">newup</b>
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-2.png" alt="图片加载失败">
                </div>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-6.png" alt="图片加载失败">
                </div>
                <div class="img-container">
                    <img src="@/assets/img/pro/use-7.png" alt="图片加载失败">
                </div>
                <p>
                    注：慢速绑定最多绑定两个设备，若需要绑定新的设备请在
                    <b style="color:chocolate;">RCN-Pro->绑定</b>
                    删除无用的设备
                </p>
            </div>
            <div v-if="activeTab === '常见问题'" class="tab-pane">

                <p>
                    1.问：我已经购买了Pro为什么开房间还是显示无权使用？
                    <br><br>
                    答：请试着在当前游戏设备上重新登录Pro网站或更换网络<br>
                </p>
                <br>

                <p>
                    2.问：我在使用S房时闪退情况频发，且有时候创建房间会卡住
                    <br><br>
                    答：可能是当前使用的服务器出现了问题，请根据下图更改节点
                <div class="img-container"><img src="@/assets/img/pro/节点修改.png" alt="图片加载失败"></div>
                </p>
                <br>

                <p>
                    3.问：我在使用慢速绑定时出现了“绑定码无法对应IP”的错误
                </p>
                <div class="img-container">
                    <img src="@/assets/img/pro/慢绑错误2.png" alt="图片加载失败">
                </div>
                <p>
                    答：请试着在当前游戏设备上登录Pro网站后再进行慢速绑定
                </p>
                <br>

                <p>
                    4.待补充
                </p>
            </div>
            <div v-if="activeTab === '反馈'" class="tab-pane">

                <p>
                    RELAY-CN交流群：<br>
                    885925961 
                </p>
                <br>
                <p>
                    Pro交流群：<br>
                    414204970
                </p>
            
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
</style>