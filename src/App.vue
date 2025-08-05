<script setup lang="ts">
import { ref } from 'vue';
import { Button as TButton, Icon as TIcon, Menu as TMenu, MenuItem as TMenuItem, Space as TSpace, Typography as TTypography } from 'tdesign-vue-next';
</script>

<template>
    <div class="min-h-screen bg-gradient-to-br from-blue-50 to-purple-50  text-gray-800">
        <!-- 导航栏 -->
        <div class="sticky top-0 z-50 bg-white/80 backdrop-blur-md shadow-sm">
            <div class="container mx-auto px-4">
                <div class="flex items-center justify-between h-16">
                    <!-- 品牌部分 -->
                    <div class="flex items-center space-x-2">
                        <t-icon name="user" class="text-blue-600" />
                        <span class="font-bold text-xl text-blue-600">XJ</span>
                    </div>
                    
                    <!-- 导航菜单 -->
                    <t-menu mode="horizontal" class="flex justify-center flex-grow">
                        <t-menu-item>首页</t-menu-item>
                        <t-menu-item>关于我</t-menu-item>
                        <t-menu-item>项目</t-menu-item>
                        <t-menu-item>联系方式</t-menu-item>
                    </t-menu>
                    
                    <!-- 操作按钮 -->
                    <div>
                        <t-button variant="primary" class="bg-blue-600 hover:bg-blue-700">
                            联系我
                        </t-button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 英雄区域 -->
        <div class="container mx-auto px-4 py-20 text-center">
            <div
                class="w-32 h-32 mx-auto rounded-full bg-gradient-to-br from-blue-400 to-purple-500 mb-6 flex items-center justify-center shadow-lg animate-pulse">
                <t-icon name="user" size="48" class="text-white" />
            </div>
            <t-typography-title
                class="text-4xl md:text-5xl font-bold mb-4 text-transparent bg-clip-text bg-gradient-to-r from-blue-600 to-purple-600">
                你好，我是 XJ
            </t-typography-title>
            <t-typography-paragraph class="text-xl text-gray-600 max-w-2xl mx-auto mb-8">
                热爱技术的开发者 | 致力于创建优雅且实用的数字体验
            </t-typography-paragraph>
            <t-space size="large" class="justify-center">
                <t-button variant="primary" size="large" class="bg-blue-600 hover:bg-blue-700">
                    查看我的项目
                </t-button>
                <t-button variant="default" size="large" class="border-blue-600 text-blue-600 hover:bg-blue-50">
                    了解更多
                </t-button>
            </t-space>
        </div>

        <!-- 关于我 -->
        <div class="container mx-auto px-4 py-16 bg-white rounded-xl shadow-md my-12">
            <t-typography-title class="text-3xl font-bold mb-8 text-center">关于我</t-typography-title>
            <div class="grid md:grid-cols-2 gap-8 items-center">
                <div class="bg-blue-50 p-8 rounded-lg">
                    <t-typography-paragraph class="text-gray-700 mb-4">
                        我是一名充满热情的开发者，专注于前端技术和用户体验设计。我喜欢创造既美观又实用的Web应用，不断探索新的技术和设计趋势。
                    </t-typography-paragraph>
                    <t-typography-paragraph class="text-gray-700 mb-4">
                        我的技术栈包括Vue.js、React、TypeScript、Tailwind CSS等，并且我始终保持学习的心态，乐于接受新的挑战。
                    </t-typography-paragraph>
                    <t-typography-paragraph class="text-gray-700">
                        除了编程，我还喜欢摄影、旅行和品尝美食。这些爱好不仅丰富了我的生活，也为我的创作提供了源源不断的灵感。
                    </t-typography-paragraph>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="bg-purple-50 p-6 rounded-lg text-center transform transition hover:scale-105">
                        <t-icon name="code" size="32" class="text-purple-600 mx-auto mb-2" />
                        <h3 class="font-bold mb-1">前端开发</h3>
                        <p class="text-sm text-gray-600">Vue.js, React, TypeScript</p>
                    </div>
                    <div class="bg-green-50 p-6 rounded-lg text-center transform transition hover:scale-105">
                        <t-icon name="paintbrush" size="32" class="text-green-600 mx-auto mb-2" />
                        <h3 class="font-bold mb-1">UI/UX设计</h3>
                        <p class="text-sm text-gray-600">Figma, Tailwind CSS</p>
                    </div>
                    <div class="bg-yellow-50 p-6 rounded-lg text-center transform transition hover:scale-105">
                        <t-icon name="database" size="32" class="text-yellow-600 mx-auto mb-2" />
                        <h3 class="font-bold mb-1">后端基础</h3>
                        <p class="text-sm text-gray-600">Node.js, Express</p>
                    </div>
                    <div class="bg-red-50 p-6 rounded-lg text-center transform transition hover:scale-105">
                        <t-icon name="camera" size="32" class="text-red-600 mx-auto mb-2" />
                        <h3 class="font-bold mb-1">摄影爱好者</h3>
                        <p class="text-sm text-gray-600">风景, 人像, 街头</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- 项目展示 -->
        <div class="container mx-auto px-4 py-16">
            <t-typography-title class="text-3xl font-bold mb-8 text-center">我的项目</t-typography-title>
            <div class="grid md:grid-cols-3 gap-8">
                <div
                    class="bg-white rounded-xl shadow-md overflow-hidden transform transition hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-blue-200 flex items-center justify-center">
                        <t-icon name="project" size="48" class="text-blue-500" />
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-xl mb-2">项目一</h3>
                        <p class="text-gray-600 mb-4">这是一个使用Vue.js和Tailwind CSS构建的响应式Web应用，专注于用户体验和性能优化。</p>
                        <t-button variant="text" class="text-blue-600">查看详情</t-button>
                    </div>
                </div>
                <div
                    class="bg-white rounded-xl shadow-md overflow-hidden transform transition hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-purple-200 flex items-center justify-center">
                        <t-icon name="app" size="48" class="text-purple-500" />
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-xl mb-2">项目二</h3>
                        <p class="text-gray-600 mb-4">这是一个使用React和TypeScript开发的单页应用，集成了多种API和第三方服务。</p>
                        <t-button variant="text" class="text-purple-600">查看详情</t-button>
                    </div>
                </div>
                <div
                    class="bg-white rounded-xl shadow-md overflow-hidden transform transition hover:scale-105 hover:shadow-lg">
                    <div class="h-48 bg-green-200 flex items-center justify-center">
                        <t-icon name="website" size="48" class="text-green-500" />
                    </div>
                    <div class="p-6">
                        <h3 class="font-bold text-xl mb-2">项目三</h3>
                        <p class="text-gray-600 mb-4">这是一个使用Next.js构建的静态网站，具有优秀的SEO性能和加载速度。</p>
                        <t-button variant="text" class="text-green-600">查看详情</t-button>
                    </div>
                </div>
            </div>
        </div>

        <!-- 联系方式 -->
        <div
            class="container mx-auto px-4 py-16 bg-gradient-to-r from-blue-600 to-purple-600 text-white rounded-xl shadow-lg my-12">
            <t-typography-title class="text-3xl font-bold mb-8 text-center">联系我</t-typography-title>
            <div class="max-w-2xl mx-auto text-center">
                <t-typography-paragraph class="mb-8 text-white/90">
                    如果你对我的项目感兴趣，或者有任何合作机会，欢迎随时联系我！
                </t-typography-paragraph>
                <t-space size="large" class="justify-center mb-8">
                    <t-button variant="text" class="text-white hover:bg-white/10 rounded-full w-12 h-12 p-0">
                        <t-icon name="github" size="24" />
                    </t-button>
                    <t-button variant="text" class="text-white hover:bg-white/10 rounded-full w-12 h-12 p-0">
                        <t-icon name="linkedin" size="24" />
                    </t-button>
                    <t-button variant="text" class="text-white hover:bg-white/10 rounded-full w-12 h-12 p-0">
                        <t-icon name="twitter" size="24" />
                    </t-button>
                    <t-button variant="text" class="text-white hover:bg-white/10 rounded-full w-12 h-12 p-0">
                        <t-icon name="email" size="24" />
                    </t-button>
                </t-space>
                <t-button variant="primary" size="large" class="bg-white text-blue-600 hover:bg-blue-50">
                    发送邮件
                </t-button>
            </div>
        </div>

        <!-- 页脚 -->
        <footer class="bg-gray-900 text-white py-8">
            <div class="container mx-auto px-4 text-center">
                <p>© 2023 XJ. 保留所有权利。</p>
            </div>
        </footer>
    </div>
</template>

<style scoped>
/* 自定义滚动条 */
::-webkit-scrollbar {
    width: 8px;
}

::-webkit-scrollbar-track {
    background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
    background: #888;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: #555;
}
</style>