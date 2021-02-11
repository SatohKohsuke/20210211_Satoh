<template>
  <div class="post-number">
        <input v-model="text" placeholder="郵便番号(ハイフンなし)">
        <button @click="search">検索</button>
        <p class="address">住所：{{ streetaddress }}</p>
  </div>
</template>

<script>
import axios from "axios";



export default {
  data() {
    return {
      apikey: "FntgQMfS0Cx9pZ8A8aSpTJksncx853dmuESJMdO",
      streetaddress: "",
    };
  },
  methods: {
    search() {
      let url = "https://apis.postcode-jp.com/api/v3/postcodes/"+this.text+"?apikey="+this.apikey;
      axios.get(url).then((res) => {
      this.streetaddress = res.data.allAddress;
      });
    },
  },
}
</script>