<script setup lang="ts">

</script>

<template>
  <t-typography-title>欢迎来到 XJ の 神秘主页</t-typography-title>
  <t-head-menu v-model="menu1Value" theme="light" @change="changeHandler">
    <template #logo>
      <img height="28" src="https://tdesign.gtimg.com/site/baseLogo-light.png" alt="logo" />
    </template>
    <t-menu-item value="item1"> 菜单1 </t-menu-item>
    <t-menu-item value="item2"> 菜单2 </t-menu-item>
    <t-menu-item value="item4" :disabled="true"> 禁用菜单 </t-menu-item>
    <template #operations>
      <t-button variant="text" shape="square">
        <template #icon><t-icon name="search" /></template>
      </t-button>
      <t-button variant="text" shape="square">
        <template #icon><t-icon name="mail" /></template>
      </t-button>
      <t-button variant="text" shape="square">
        <template #icon><t-icon name="user" /></template>
      </t-button>
      <t-button variant="text" shape="square">
        <template #icon><t-icon name="ellipsis" /></template>
      </t-button>
    </template>
  </t-head-menu>
</template>


<style scoped>

</style>