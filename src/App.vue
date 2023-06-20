<template>
  <v-app :class="dark ? 'f-dark' : ''" style="font-family: Roboto, sans-serif">
    <!--      <app-index-tips :dark="dark"></app-index-tips>-->
    <v-app-bar
        app
        elevate-on-scroll
        clipped-left
        style="
        transition: 0s ease background-color,
          280ms cubic-bezier(0.4, 0, 0.2, 1) box-shadow;
      "
        :dark="dark"
        :color="dark ? 'hsl(0,0%,7%)' : 'hsl(0,0%,100%)'"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>{{ header.title }}</v-toolbar-title>
      <el-divider direction="vertical"></el-divider>

      <v-spacer></v-spacer>
      <v-btn icon @click.stop="dark ? offDarkMode() : onDarkMode()">
        <v-icon>mdi-{{ header.icon.darkmode }}</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" floating app clipped :dark="dark">
      <f-navbar-list></f-navbar-list>
    </v-navigation-drawer>

    <v-main :dark="dark">
      <canvas id="canvas" class="snow"></canvas>
      <f-main-title></f-main-title>
      <v-container class="f-container">
        <f-main-about :dark="dark"></f-main-about>
        <f-main-chips :dark="dark"></f-main-chips>
        <f-contact
            style="display: block; opacity: 1; z-index: 1"
            :dark="dark"
        ></f-contact>
        <f-main-site  :dark="dark"></f-main-site>
        <f-bot-steps :dark="dark"></f-bot-steps>
        <f-donate :dark="dark"></f-donate>
        <f-donates :dark="dark"></f-donates>
        <f-pick-show :dark="dark"></f-pick-show>
          <v-divider
                  inset
          ></v-divider>
        <v-list-item :dark="dark"><v-list-item-content><v-list-item-title class="headline">友情链接</v-list-item-title></v-list-item-content></v-list-item>
        <friend-links :dark="dark"></friend-links>
          <v-divider
                  inset
          ></v-divider>
          <v-list-item :dark="dark"><v-list-item-content><v-list-item-title class="headline">教程推荐</v-list-item-title></v-list-item-content></v-list-item>
          <tutorial :dark="dark"></tutorial>
          <v-divider
                  inset
          ></v-divider>
        <f-footer :dark="dark"></f-footer>

        <aplayer :audio="audio" :lrcType="3" fixed :dark="dark" />
      </v-container>
      <el-backtop
          :dark="dark"
          visibility-height="150"
          :right="10"
          :bottom="100"
      >
        <div

            style="
             {
              height: 100%;
              width: 100%;
              box-shadow: 0 0 6px rgba(0, 0, 0, 0.12);
              text-align: center;
              line-height: 40px;
              color: #fb7299;
            }
          "
        >
          ↑
        </div>
      </el-backtop>
    </v-main>
  </v-app>
</template>

<script>


import Tutorial from "./components/Tutorial.vue";

console.log("%c 邀请您加入我们的开发 %c ".concat("QQ2110146041", " ").concat("添加信息:开发路🐫", " %c"), 'background: #35495e; padding: 1px; border-radius: 3px 0 0 3px; color: #fff', 'background: #fb7299; padding: 1px; border-radius: 0 3px 3px 0; color: #fff', 'background: transparent');

import Darkmode from "./assets/darkmode";
// import Snow from  "./assets/snow"
import FNavbarList from "./components/NavbarList";
import FMainTitle from "./components/Title";
import FMainAbout from "./components/About";
import FMainChips from "./components/Chips";
import FContact from "./components/Contact";
import FMainSite from "./components/Site";
import FDonate from "./components/Donate";
import FFooter from "./components/Footer";
import FDonates from "./components/Donates";
import FPickShow from "./components/PickShow";
import FBotSteps from "./components/BotSetps.vue";
import FriendLinks from "@/components/FriendLinks.vue";
import axios from "axios";
// import FPicslide from "./components/Picslide";


export default {
  name: "App",
  metaInfo: require("./data/meta.json"),
  components: {
      Tutorial,
    FriendLinks,
    // FMainNewYear,
    FNavbarList,
    FMainTitle,
    FMainAbout,
    FMainChips,
    FMainSite,
    FContact,
    FDonate,
    FDonates,
    FFooter,
    // FLinkPage,
    // FPicslide,
    FPickShow,
    FBotSteps,
  },

  data: () => ({
    onDarkMode() {},
    offDarkMode() {},
    header: require("./data/header.json"),
    audio: [],
    dark: false,
    dialog: false,
    // snow:false,
    drawer: null,
  }),
  methods: {

  },
  async created(){
    try {
      const response = await axios.get("https://api.etherealcraft.cn/api/audio");
      this.audio = response.data;
    } catch (error){
      console.log(error);
    }
  },
  mounted() {
    Darkmode(this);
    // Snow(this);

  },
};
</script>

<style src="./assets/global.css"></style>
