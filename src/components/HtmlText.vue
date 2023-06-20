<template>
    <div>
        <div v-if="loading">Loading...</div>
        <div v-else-if="error">{{ error }}</div>
        <div v-else v-html="htmlContent"></div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name:"HtmlText",
    props: {
    url: {
      type: String,
      required: true,
    },
  },
    data() {
        return {
            htmlContent: '',
            loading: false,
            error: ''
        };
    },
    mounted() {
        this.fetchHtmlContent();
    },
    methods: {
        fetchHtmlContent() {
            this.loading = true;
            axios
        .get(this.url)
        .then((response) => {
          this.loading = false;
          this.htmlContent = response.data.content;
        })
        .catch((error) => {
          this.loading = false;
          this.error = error.response.data.error;
        });
    },
},
};
</script>
