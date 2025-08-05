<script setup lang="ts">
import type { UserOptions, MenuItem } from '@/types/appheader';
import { useRoute, useRouter } from 'vue-router';
import { onMounted, ref, watch } from 'vue';
import { useUserStore } from '@/stores';
import { storeToRefs } from 'pinia';
import Settings from '@/components/AppSettings.vue';
import themeMode from '@/utils/themeMode';

const user = useUserStore();
const route = useRoute();
const router = useRouter();
const page = ref(route.path.split('/')[1]);
const MobileMenyVisible = ref(false);
const collapsed = ref(false);
const { userData, loginStatus } = storeToRefs(user);
const theme = ref<'auto' | 'light' | 'dark'>('light');

const userOptions: UserOptions[] = [
  { content: '个人中心', value: 'person', action: () => router.push('/user') },
  {
    content: '赛事管理',
    value: 'manager-center',
    action: () => {
      router.push('/manager');
    },
  },
  { content: '退出登录', value: 'logout', action: () => user.logout() },
];
const userClickHandler = (data: UserOptions) => data.action();
const menu: MenuItem[] = [
  { index: '', name: '首页', path: '/', status: 'open', access: 'all' },
  { index: 'manager', name: '赛事管理', path: '/manager', status: 'open', access: 'all' },
];

onMounted(() => {
  page.value = route.path.split('/')[1];
  theme.value = themeMode() || 'auto';
  watch(theme, (value) => themeMode(value, true));
  watch(
    () => route.path,
    () => {
      page.value = route.path.split('/')[1];
    },
  );
});
</script>

<template>
  <t-head-menu theme="light" defaultValue="" v-model:value="page">
    <template #logo>
      <img style="height: 24px" src="/text-logo.svg" alt="logo" />
    </template>
    <t-space>
      <div v-for="(item, idx) in menu" :key="idx" class="hidden md:block">
        <div v-if="item.status !== 'closed'">
          <t-menu-item
            :value="item.index"
            :router="router"
            routerLink
            :to="{ path: item.path }"
            :disabled="item.status === 'disabled'"
            >{{ item.name }}
          </t-menu-item>
        </div>
        <div v-else></div>
      </div>
    </t-space>
    <template #operations>
      <div class="hidden md:block">
        <t-space>
          <t-select v-model:value="theme" :borderless="true" defaultValue="auto" :autoWidth="true">
            <t-option title="跟随系统" label="跟随系统" value="auto">
              <t-space :size="5">
                <t-icon name="system-setting" size="medium" />
                跟随系统
              </t-space>
            </t-option>
            <t-option title="白天模式" label="白天模式" value="light">
              <t-space :size="5">
                <t-icon name="sunny" size="medium" />
                白天模式
              </t-space>
            </t-option>
            <t-option title="黑夜模式" label="黑夜模式" value="dark">
              <t-space :size="5">
                <t-icon name="moon" size="medium" />
                黑夜模式
              </t-space>
            </t-option>
          </t-select>
          <t-dropdown :options="userOptions" @click="userClickHandler" v-if="loginStatus">
            <t-button variant="text" shape="circle">
              <t-avatar size="32px" :image="userData.profile.avatar"></t-avatar>
            </t-button>
          </t-dropdown>
          <t-button variant="text" shape="circle" @click="user.login()" v-else>
            <t-avatar size="32px">
              <template #icon><t-icon name="user-1" size="large" /></template>
            </t-avatar>
          </t-button>
        </t-space>
      </div>
      <div class="block md:hidden">
        <t-button theme="default" variant="text" shape="square" @click="MobileMenyVisible = true">
          <template #icon>
            <t-icon name="menu-fold" size="large" />
          </template>
        </t-button>
      </div>
    </template>
  </t-head-menu>
  <!--手机端使用的抽屉式菜单-->
  <t-drawer v-model:visible="MobileMenyVisible" size="60%" placement="left" :lazy="true">
    <template #header>
      <div @click="user.logout()" v-if="loginStatus">
        <t-space size="small" class="items-center">
          <t-avatar size="32px" :image="userData.profile.avatar" />
          <span class="text-bold">{{ userData.profile.nickname }}</span>
        </t-space>
      </div>
      <div v-else>
        <t-space size="small" class="items-center">
          <t-avatar size="32px">
            <template #icon><t-icon name="user-1" size="large" /></template>
          </t-avatar>
          <span class="text-bold">未登录</span>
        </t-space>
      </div>
    </template>
    <div class="overflow-x-hidden">
      <t-menu v-model:value="page" :collapsed="collapsed" destroy-on-close>
        <t-space direction="vertical" class="w-full">
          <div v-for="item in menu" :key="item.index" class="w-full">
            <div v-if="item.status !== 'closed'" class="w-full">
              <t-menu-item
                :value="item.index"
                :router="router"
                routerLink
                :to="item.path"
                :disabled="item.status === 'disabled'"
                >{{ item.name }}</t-menu-item
              >
            </div>
            <div v-else></div>
          </div>
        </t-space>
      </t-menu>
    </div>
    <template #footer>
      <Settings />
    </template>
  </t-drawer>
</template>
