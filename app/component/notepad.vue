<template lang="html">
  <div>
    <div class="large-border">
      <div class="small-border">
        <figure class="notepad-figure">
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
import VueLocalStorage from 'vue-localstorage';
import Vue from 'vue';
import $ from 'jquery';

Vue.use(VueLocalStorage)

$("textarea").keydown(function(e) {
    if(e.keyCode === 9) {
        var start = this.selectionStart;
            end = this.selectionEnd;

        var $this = $(this);

        $this.val($this.val().substring(0, start)
                    + "\t"
                    + $this.val().substring(end));

        this.selectionStart = this.selectionEnd = start + 1;

        e.preventDefault();
        e.stopPropagation();

        return false;
    }
});

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
  .notepad-figure {
    margin-left: 2em;
    height: 600px;
  }
  textarea {
    overflow-y: scroll;
    padding: 1em 0;
  }
</style>
