<template>
  <div class="f-chips mx-2">
      <v-card-text>关于服务器的详细内容请查看<a href="https://www.etherealcraft.cn/wiki">Wiki</a>,进行更多了解。</v-card-text>
    <v-chip
      class="ma-1"
      v-for="(item, index) in shuffle(tag)"
      :key="index"
      :dark="dark"
    >
      <v-avatar left>
        <v-icon>mdi-{{ item.icon }}</v-icon>
      </v-avatar>
      {{ item.text }}
    </v-chip>
    <v-chip
      class="ma-1"
      v-for="(item, index) in shuffle(language)"
      :key="index + tag.length"
      :dark="dark"
    >
      <v-avatar left :style="'background: ' + item.color"></v-avatar>
      {{ item.name }}
    </v-chip>
    <el-divider></el-divider>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tag: require("../data/chips.json"),
      language: [],
    };
  },
  methods: {
    shuffle: function (arr) {
      var len = arr.length;
      for (var i = 0; i < len - 1; i++) {
        var index = parseInt(Math.random() * (len - i));
        var temp = arr[index];
        arr[index] = arr[len - i - 1];
        arr[len - i - 1] = temp;
      }
      return arr;
    },
  },
  props: {
    dark: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style>
.f-chips {
  margin: 14px -4px 14px;
}
</style>
