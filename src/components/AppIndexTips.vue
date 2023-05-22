<template>
    <v-dialog v-model="appIndexTips" :dark="dark" :max-width="isMobile ? 300 : 500" persistent>
        <template v-for="tip in tips">
            <v-card :key="tip.title" :dark="dark" class="headline">
                <v-card-title>{{ tip.title }}</v-card-title>
                <v-card-subtitle>{{ tip.subtitle }}</v-card-subtitle>
                <v-card-text v-html="tip.text"></v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <div class="confirm-container">
                        <v-btn
                            class="mx-2 mx-auto d-flex justify-center v-btns"
                            color="#fb7299"
                            dark
                            fab
                            small
                            @click="closeDialog"
                        >
                            <v-icon dark>mdi-check</v-icon>
                        </v-btn>
                    </div>
                    <v-spacer></v-spacer>
                </v-card-actions>
            </v-card>
        </template>
    </v-dialog>
</template>
<script>
import axios from "axios";
// 获取主页面的滚动位置


export default {
    name: "AppIndexTips",
    data() {
        return {
            appIndexTips: false,
            lastShown: null,
            isMobile: false,
            tips: [],
        };
    },
    props: {
        dark: {
            type: Boolean,
            required: true,
        },
    },
    created() {
        this.lastShown = localStorage.getItem("lastShown");
        if (!this.lastShown || Date.now() - this.lastShown >= 24 * 60 * 60 * 1000) {
            this.appIndexTips = true;
        }
        this.isMobile = this.$vuetify.breakpoint.mobile;
    },

    methods: {
        closeDialog() {
            const scrollPosition = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0;
            this.appIndexTips = false;
            this.lastShown = Date.now();
            localStorage.setItem("lastShown", this.lastShown);
            // 恢复主页面的滚动能力，并将滚动位置设置回去
            document.body.style.overflow = null;
            window.scrollTo(0, scrollPosition);
        },
    },
    async mounted() {
        try {
            const response = await axios.get(
                "https://api.etherealcraft.cn/api/tips"
            );
            this.tips = response.data;
        } catch (error) {
            console.log(error);
        }
    },
};
</script>
<style scoped>
.confirm-container {
    position: fixed;
    left: 50%;
    bottom: 20px;
    transform: translateX(-50%);
    z-index: 9999;
    width: 100%;
    text-align: center;
}

.v-btns {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    bottom: -20px;
}
</style>