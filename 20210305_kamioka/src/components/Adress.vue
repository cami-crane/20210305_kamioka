<template>
  <div>
    <input type="text" v-model="zip" />
    <button @click="getAddress">住所自動入力</button>
    <p>Adress: {{ address }}</p>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "Adress",
  data() {
    return {
      zip: ""
    };
  },
  computed: {
    ...mapState({
      zip: state => state.zip
    }),
    address() {
      return this.$store.state.zip.address;
    }
  },
  methods: {
    getAddress() {
      this.$store.commit("getAddress", this.zip);
      this.$store.dispatch("getAddressAction");
    }
  }
};
</script>