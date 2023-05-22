<template>
  <v-card class="pt-4" :dark="dark" elevation="4" style="background: none">
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="headline">急招人员</v-list-item-title>
        <v-list-item-subtitle>Urgently recruit people</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
    <v-card-text>
        目前我们的游戏服务器正在高速发展阶段，但是我们面临一个重要问题：缺少经验丰富的肝帝大佬和专业的开发人员、美术人员等来加速服务器的发展。我们希望找到那些热爱游戏并具有扎实技术背景的开发者，来加入我们的团队并共同推动服务器的进步和发展。如果您对此有兴趣，请不要犹豫，加入我们的游戏社群，与我们一起创造一个更加完美的游戏世界！
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    color: "#7d61cd",
    link: "https://afdian.net/@flyingsky",
    text: "爱发电",
  }),
  props: {
    dark: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
<style></style>
