<template>
    <v-card class="pt-4 mb-4" :dark="dark" elevation="1" style="background: none">
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="headline">联系我们</v-list-item-title>
                <v-list-item-subtitle>Contact</v-list-item-subtitle>
            </v-list-item-content>
        </v-list-item>
        <div class="px-2 pb-2">
            <v-row no-gutters>
                <v-col cols="6" class="px-2">
                    <div class="text-center">
                        <v-dialog v-model="dialogVisible" width="500">
                            <template v-slot:activator="{on,attrs}">
                                <v-card
                                        class="contactsonw"
                                        outlined
                                        elevation="4"
                                        style="background: none; "
                                        :dark="dark"
                                        v-bind="attrs"
                                        v-on="on"
                                >
                                    <v-card-title class="headline">腐竹</v-card-title>
                                    <v-card-subtitle>章鱼蛋</v-card-subtitle>
                                </v-card>
                            </template>
                            <v-card :dark="dark">
                                <v-card-title
                                        style="background-color: #fb7299"
                                        class="text-h5 lighten-2"
                                >{{ botsetps.title }}</v-card-title>
                                <v-card-text>{{ botsetps.contact.contact1 }}</v-card-text>
                                <v-spacer></v-spacer>
                                <v-card-actions>
                                    <v-btn color="#fb7299" text @click="dialogVisible = false">
                                        <v-icon>mdi-close</v-icon>
                                        关闭
                                    </v-btn>
                                    <v-btn color="#fb7299" text @click="connect">
                                        <v-icon>mdi-lan-connect</v-icon>
                                        联系
                                    </v-btn>
                                </v-card-actions>
                            </v-card>
                        </v-dialog>
                    </div>
                </v-col>
            </v-row>
        </div>
    </v-card>
</template>
<script>
import botsetps from "@/data/botsetps.json";

export default {
    data() {
        return {
            dialogVisible: false,
        };
    },
    methods: {
        connect() {
            window.open("tencent://message/?uin=2665405745&Site=&Menu=yes");
        },
    },
    props: {
        dark: {
            type: Boolean,
            required: true,
        },
    },
    computed: {
        botsetps() {
            return botsetps;
        },
    },
};
</script>
<style scoped>
.contactsonw {
    z-index: 1;
    opacity: 0.8;
}
</style>