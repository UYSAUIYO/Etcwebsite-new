<template>
  <div style="background: none" class="bots" :dark="dark">
    <v-card style="background:none">
      <v-toolbar flat color="#fb7299" :dark="dark">
        <v-toolbar-title>审核单元</v-toolbar-title>
        <v-card-subtitle>Beta</v-card-subtitle>
      </v-toolbar>
      <v-tabs vertical :dark="dark">
        <v-tabs-slider color="#fb7299"></v-tabs-slider>
        <v-tab left>
          <v-icon>mdi-account-alert</v-icon>
          基础要求
        </v-tab>
        <v-tab>
          <v-icon left> mdi-chip </v-icon>
          红石
        </v-tab>
        <v-tab>
          <v-icon left> mdi-bank </v-icon>
          后勤
        </v-tab>
        <v-tab>
          <v-icon left> mdi-apps </v-icon>
          建筑
        </v-tab>

        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-title>审核规定</v-card-title>
            <v-card-subtitle>审核流程介绍</v-card-subtitle>
            <v-card-text>

            </v-card-text>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-title>红石</v-card-title>
            <v-card-subtitle>审核流程介绍</v-card-subtitle>
           <v-card-text></v-card-text>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-text>
              <v-card-title>后勤要求</v-card-title>
              <v-card-subtitle>审核流程介绍</v-card-subtitle>
              <v-card-text></v-card-text>
            </v-card-text>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-text>
              <v-card-title>建筑</v-card-title>
              <v-card-subtitle>审核要求介绍 Beta</v-card-subtitle>

            </v-card-text>
          </v-card>
        </v-tab-item>
      </v-tabs>
    </v-card>
  </div>
</template>

<script>

export default {
  name: "BotSetps",
  components: {},
  data() {
    return {
    };
  },
  watch:{
    loader (){
      const l = this.loader
      this[l] = !this[l]
      setTimeout(() => (this[l] = false), 3000)
      setTimeout(function (){
        window.open("https://wj.etherealcraft.cn/user/register")
      },3000)
    }
  },
  methods: {
    tftip(){
      const tfttiph = this.$createElement;
      this.$notify({
        title:'考察期',
        message:tfttiph('i','考察期指的是新成员入服七天内的综合表现。'),
        type:'warning',
        position:'bottom-left',
        showClose:false,
        offset:100
      })
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

<style scoped>
/*.retie {*/
/*  text-decoration: none;*/
/*}*/
/* .bots{
  display: table-cell;
  max-width: 550px;
} */
.login {
  background-color: #fb7299;
}
</style>
