<template>
	<div>
    <h3>{{album.TITLE}}</h3>
    <img :src="album.IMAGE" :alt="album.TITLE">
    <br>    
    <button type="button" @click="toggle">Album Details</button>
    <div v-show="showDetails" v-html="album.DESCRIPTION"></div>
    <br>
    <hr>
	</div>
</template>

<script>
export default {
  props: ["album"],
  data() {
    return {
      showDetails: false
    };
  },
  methods: {
    toggle() {
      this.showDetails = !this.showDetails;
    }
  }
};
</script>

<style scoped>
div {
  max-width: 500px;
  margin: 0 auto;
}
</style>
