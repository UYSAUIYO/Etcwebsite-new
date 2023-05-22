<template>
  <v-card
    class="pt-4 donatesnow"
    :dark="dark"
    elevation="4"
    style="background: none"
  >
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="headline">服务器网络开发进度</v-list-item-title>
        <v-list-item-subtitle>server web development progress</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
    <v-card-text>
        项目需要开发人员进行官网和审核系统的维护，同时还有新的机器人正在迭代，我们需要热爱游戏的开发者加入我们的团队，一起创造更多精彩的内容，展示游戏的美好。
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data(){

  },
  props: {
    dark: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
<style></style>
