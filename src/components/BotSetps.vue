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
                <HtmlText :url="requestNamu1"></HtmlText>
            </v-card-text>
              <v-spacer></v-spacer>
              <v-divider></v-divider>
              <v-container>
                  <v-btn @click="openDialog" color="#ff80ab">
                  <v-icon>mdi-login</v-icon>
                      注册
                  </v-btn>
              </v-container>
              <v-dialog v-model="dialogVisible" :dark="dark" max-width="500px">
                  <v-card>
                      <div class="bililipink">
                          <v-card-title class="headline text-h5 lighten-2 ">
                              提示
                          </v-card-title>
                          <v-card-subtitle>tips</v-card-subtitle></div>
                      <v-divider></v-divider>
                      <v-card-text>
                          是否已经阅读了审核基础的要求,已经阅读后请等待5秒钟进行审核的注册。
                      </v-card-text>
                      <v-divider></v-divider>
                      <v-card-actions>
                          <v-spacer></v-spacer>
                          <v-btn @click="closeDialog" color="#ff80ab">
                              <v-icon>mdi-close</v-icon>
                              关闭
                          </v-btn>
                          <v-btn color="#ff80ab" :disabled="countdown > 0" @click="redirectToLink">
                              <v-progress-circular v-if="countdown > 0" indeterminate color="#ff80ab"></v-progress-circular>
                              <div v-else>
                                  <v-icon >mdi-check</v-icon>确定</div>
                          </v-btn>
                      </v-card-actions>
                  </v-card>
              </v-dialog>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-title>红石</v-card-title>
            <v-card-subtitle>审核流程介绍</v-card-subtitle>
           <v-card-text>
               <HtmlText :url="requestNamu2"></HtmlText>
           </v-card-text>
              <v-spacer></v-spacer>
              <v-divider></v-divider>
              <v-container>
                  <v-btn @click="openDialog1" color="#ff80ab">
                      <v-icon>mdi-login</v-icon>
                      填写问卷
                  </v-btn>
              </v-container>
              <v-dialog v-model="dialogVisible1" :dark="dark" max-width="500px">
                  <v-card>
                      <div class="bililipink">
                          <v-card-title class="headline text-h5 lighten-2 ">
                              提示
                          </v-card-title>
                          <v-card-subtitle>tips</v-card-subtitle></div>
                      <v-divider></v-divider>
                      <v-card-text>
                          是否已经阅读了审核基础的要求,已经阅读后请等待5秒钟进行审核的注册。
                      </v-card-text>
                      <v-divider></v-divider>
                      <v-card-actions>
                          <v-spacer></v-spacer>
                          <v-btn @click="closeDialog" color="#ff80ab">
                              <v-icon>mdi-close</v-icon>
                              关闭
                          </v-btn>
                          <v-btn color="#ff80ab" :disabled="countdown > 0" @click="redirectToLink1">
                              <v-progress-circular v-if="countdown > 0" indeterminate color="#ff80ab"></v-progress-circular>
                              <div v-else>
                                  <v-icon >mdi-check</v-icon>确定</div>
                          </v-btn>
                      </v-card-actions>
                  </v-card>
              </v-dialog>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-text>
              <v-card-title>后勤要求</v-card-title>
              <v-card-subtitle>审核流程介绍</v-card-subtitle>
              <v-card-text>
                  <HtmlText :url="requestNamu3"></HtmlText>
              </v-card-text>
                <v-spacer></v-spacer>
                <v-divider></v-divider>
                <v-container>
                    <v-btn @click="openDialog2" color="#ff80ab">
                        <v-icon>mdi-login</v-icon>
                        填写问卷
                    </v-btn>
                </v-container>
                <v-dialog v-model="dialogVisible2" :dark="dark" max-width="500px">
                    <v-card>
                        <div class="bililipink">
                            <v-card-title class="headline text-h5 lighten-2 ">
                                提示
                            </v-card-title>
                            <v-card-subtitle>tips</v-card-subtitle></div>
                        <v-divider></v-divider>
                        <v-card-text>
                            是否已经阅读了审核基础的要求,已经阅读后请等待5秒钟进行审核的注册。
                        </v-card-text>
                        <v-divider></v-divider>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn @click="closeDialog" color="#ff80ab">
                                <v-icon>mdi-close</v-icon>
                                关闭
                            </v-btn>
                            <v-btn color="#ff80ab" :disabled="countdown > 0" @click="redirectToLink1">
                                <v-progress-circular v-if="countdown > 0" indeterminate color="#ff80ab"></v-progress-circular>
                                <div v-else>
                                    <v-icon >mdi-check</v-icon>确定</div>
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-card-text>
          </v-card>
        </v-tab-item>
        <v-tab-item>
          <v-card flat :dark="dark">
            <v-card-text>
              <v-card-title>建筑</v-card-title>
              <v-card-subtitle>审核要求介绍 Beta</v-card-subtitle>
                <HtmlText :url="requestNamu4"></HtmlText>
            </v-card-text>
              <v-spacer></v-spacer>
              <v-divider></v-divider>
              <v-container>
                  <v-btn @click="openDialog3" color="#ff80ab">
                      <v-icon>mdi-login</v-icon>
                      填写问卷
                  </v-btn>
              </v-container>
              <v-dialog v-model="dialogVisible3" :dark="dark" max-width="500px">
                  <v-card>
                      <div class="bililipink">
                          <v-card-title class="headline text-h5 lighten-2 ">
                              提示
                          </v-card-title>
                          <v-card-subtitle>tips</v-card-subtitle></div>
                      <v-divider></v-divider>
                      <v-card-text>
                          是否已经阅读了审核基础的要求,已经阅读后请等待5秒钟进行审核的注册。
                      </v-card-text>
                      <v-divider></v-divider>
                      <v-card-actions>
                          <v-spacer></v-spacer>
                          <v-btn @click="closeDialog" color="#ff80ab">
                              <v-icon>mdi-close</v-icon>
                              关闭
                          </v-btn>
                          <v-btn color="#ff80ab" :disabled="countdown > 0" @click="redirectToLink3">
                              <v-progress-circular v-if="countdown > 0" indeterminate color="#ff80ab"></v-progress-circular>
                              <div v-else>
                                  <v-icon >mdi-check</v-icon>确定</div>
                          </v-btn>
                      </v-card-actions>
                  </v-card>
              </v-dialog>
          </v-card>
        </v-tab-item>
      </v-tabs>
    </v-card>
  </div>
</template>

<script>
import HtmlText from "./HtmlText.vue";
export default {
  name: "BotSetps",
  components: {HtmlText},
  data() {
    return {
        dialogVisible: false,
        dialogVisible1:false,
        dialogVisible2:false,
        dialogVisible3:false,
        countdown: 3,
        requestNamu1: 'https://api.etherealcraft.cn/api/html/index',
        requestNamu2: 'https://api.etherealcraft.cn/api/html/redstone' ,
        requestNamu3: 'https://api.etherealcraft.cn/api/html/logistics' ,
        requestNamu4: 'https://api.etherealcraft.cn/api/html/builder' ,
    };
  },
  props: {
    dark: {
      type: Boolean,
      required: true,
    },
  },
    methods: {
      openDialog1(){
          this.dialogVisible1 = true;
          this.startCountdown1();
      },
        openDialog2(){
            this.dialogVisible2= true;
            this.startCountdown2();
        },
        openDialog3(){
            this.dialogVisible3 = true;
            this.startCountdown3();
        },
        openDialog() {
            this.dialogVisible = true;
            this.startCountdown();
        },
        closeDialog() {
            this.dialogVisible1=false;
            this.dialogVisible2=false;
            this.dialogVisible3=false;
            this.dialogVisible = false;
        },
        redirectToLink1(){
            window.open("https://wj.etherealcraft.cn/s/HXNCc1");
            console.log("Redirecting to link...");
            this.dialogVisible1=false;
            this.dialogVisible2=false;
            this.dialogVisible3=false;
            this.dialogVisible = false;
        },
        redirectToLink3(){
            window.open("https://wj.etherealcraft.cn/s/RprmzU");
            console.log("Redirecting to link...");
            this.dialogVisible1=false;
            this.dialogVisible2=false;
            this.dialogVisible3=false;
            this.dialogVisible = false;
        },

        redirectToLink() {
            window.open("https://wj.etherealcraft.cn/user/login");
            console.log("Redirecting to link...");
            this.dialogVisible1=false;
            this.dialogVisible2=false;
            this.dialogVisible3=false;
            this.dialogVisible = false;
        },
        startCountdown() {
            const timer = setInterval(() => {
                if (this.countdown > 0) {
                    this.countdown--;
                } else {
                    clearInterval(timer);
                }
            }, 1000);
        },
        startCountdown1() {
            const timer = setInterval(() => {
                if (this.countdown > 0) {
                    this.countdown--;
                } else {
                    clearInterval(timer);
                }
            }, 1000);
        }
        ,
        startCountdown2() {
            const timer = setInterval(() => {
                if (this.countdown > 0) {
                    this.countdown--;
                } else {
                    clearInterval(timer);
                }
            }, 1000);
        },
        startCountdown3() {
            const timer = setInterval(() => {
                if (this.countdown > 0) {
                    this.countdown--;
                } else {
                    clearInterval(timer);
                }
            }, 1000);
        }
    }
};
</script>

<style scoped>
.bililipink{
    background-color: #ff80ab;
}
</style>
