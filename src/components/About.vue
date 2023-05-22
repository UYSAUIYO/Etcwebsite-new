<template>
    <v-card class="pt-4 " elevation="0" :dark="dark" style="background: none">
        <v-card-text class="f-text" style="max-width: 650px">
            <v-card class="mx-auto" max-width="auto">
                <v-card dark flat>
                    <v-card-title class="pa-2 pink accent-1">
                        <v-list-item>
                            <v-list-item-content>
                                <v-list-item-title class="headline"
                                >关于服务器</v-list-item-title
                                >
                                <v-list-item-subtitle>About Server</v-list-item-subtitle>
                            </v-list-item-content>
                        </v-list-item>
                    </v-card-title>
                </v-card>
                <v-card-text class="py-0 auto-height">
                    <v-timeline align-top dense>
                        <v-timeline-item v-for="request in requests" :color="request.color" :small="request.small" :key="request">
                            <v-row class="pt-1">
                                <v-col cols="4">
                                    <strong>{{ request.date }}</strong>
                                </v-col>
                                <v-col>
                                    <strong>{{ request.title }}</strong>
                                    <div class="text-caption">{{ request.subtitle }}</div>
                                </v-col>
                            </v-row>
                        </v-timeline-item>
                    </v-timeline>
                </v-card-text>
            </v-card>
        </v-card-text>
    </v-card>
</template>
<script>

import axios from "axios";

export default {
    props: {
        dark: {
            type: Boolean,
            required: true,
        },
    },
    data() {
        return {
            requests: [],
            color:''
        };
    },
    async created(){
        try {
            const response = await axios.get("https://api.etherealcraft.cn/api/about");
            this.requests = response.data;
        }catch (error){
            console.log(error)
        }
    }
};
</script>
<style scoped>
.auto-height{

}
</style>