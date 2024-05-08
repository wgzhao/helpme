<template>
    <v-navigation-drawer>
  <v-list-item title="Help me" subtitle="Toolkit"></v-list-item>
  <v-divider></v-divider>
  <v-list-item link title="图片工具" prepend-icon="mdi-image" ></v-list-item>
  <v-list-item link title="PDF转换工具" prepend-icon="mdi-file-pdf-box"></v-list-item>
  <v-list-item link title="数据换算工具" prepend-icon="mdi-calculator" to="/category/data"></v-list-item>
  <v-list-item link title="开发工具" prepend-icon="mdi-language-python" to="/category/develop"></v-list-item>
</v-navigation-drawer>
</template>
<script setup lang="ts">
</script>
