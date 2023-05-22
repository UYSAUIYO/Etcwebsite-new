<template>
    <div class="friend-links">
        <v-container>
            <v-row>
                <v-col cols="12" sm="6" md="4" v-for="link in links" :key="link.id">
                    <v-card class="elevation-10" :href="link.url" target="_blank" color="transparent" :dark="dark">
                        <v-card-text class="links-row">
                            <v-row class="no-gutters align-center" :dark="dark">
                                <v-col cols="2" class="text-center">
                                    <img :src="link.icon" class="link-icon" />
                                </v-col>
                                <v-col cols="10" :dark="dark">
                                    <div class="link-name">{{ link.name }}</div>
                                    <div class="link-description">{{ link.description }}</div>
                                </v-col>
                            </v-row>
                        </v-card-text>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script>
import axios from "axios";

export default {
    name: "FriendLinks",
    data() {
        return {
            links: [],
        };
    },
    props: {
        dark: {
            type: Boolean,
            required: true,
        },
    },
    async created() {
        try {
            const response = await axios.get("https://api.etherealcraft.cn/api/link");
            this.links = response.data;
        } catch (error) {
            console.log(error);
        }
    },
};
</script>

<style scoped>
.links-row {
    background: none;
}

.friend-links {
    /*background-color: transparent;*/
    padding: 32px 0;
    height: 330px; /* 设置容器高度 */
    overflow: auto; /* 指定滚动行为 */
}

.elevation-10 {
    /*background-color: transparent;*/
    box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.14), 0px 3px 1px rgba(0, 0, 0, 0.12), 0px 1px 5px rgba(0, 0, 0, 0.2);
}

.link-icon {
    width: 36px;
    height: 36px;
}

.link-name {
    font-size: 18px;
    font-weight: 500;
}

.link-description {
    font-size: 14px;
    /*color: rgba(0, 0, 0, 0.54);*/
}
</style>
