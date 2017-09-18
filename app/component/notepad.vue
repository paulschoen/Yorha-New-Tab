<template lang="html">
  <div>
    <div class="large-border">
      <div class="small-border">
        <figure>
          <figcaption><span>&#9632</span> Note Pad</figcaption>
          <hr style="margin: 0; width: 98%;">
          <textarea class="text-area" v-model="text"></textarea>
          <hr style="margin: 0; width: 98%;">
        </figure>
      </div>
    </div>
  </div>
</template>

<script>
import VueLocalStorage from 'vue-localstorage'
import Vue from 'vue'

Vue.use(VueLocalStorage)

export default {
  data:function(){
    return {
      text: Vue.localStorage.get('text')
    }
  },
  watch: {
    text: function (newText) {
      Vue.localStorage.set('text', newText);
      this.text = newText;
    }
  }
}
</script>

<style lang="css">
  textarea {
    overflow-y: scroll;
    padding: 1em 0;
  }
</style>
