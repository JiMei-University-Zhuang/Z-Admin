<template>
  <div class="layout">
    <LayoutSider />
    <div class="main" :class="{ 'collapsed': collapsed }">
      <LayoutHeader />
      <main class="content">
        <!-- 展示区 -->
        <router-view></router-view>
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useAppStore } from '@/stores'
import LayoutHeader from './components/Header.vue'
import LayoutSider from './components/Sider.vue'
import { storeToRefs } from 'pinia'

const appStore = useAppStore()
const { collapsed, } = storeToRefs(appStore)
</script>

<style scoped>
.layout {
  height: 100vh;
  position: relative;
}

.main {
  margin-left: 210px;
  position: relative;
  min-height: 100%;
  background: var(--el-bg-color);
  transition: margin-left 0.28s;
  z-index: 2;
}

.main.collapsed {
  margin-left: 64px;
}

.content {
  padding: 20px;
  box-sizing: border-box;
  position: relative;
  z-index: 1;
}

html.dark .main {
  background: #f0f2f5;
}
</style>