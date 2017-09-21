<template lang="html">
  <div style="padding: 0.5em">
      <div style="padding: 0" v-if="bookmarks" v-for="bookmark in bookmarks" class="fadeInLeft display-none">
        <a v-bind:href="bookmark.url" class="custom-button">
        <button style="margin-top: 0px;" type="button" class="custom-button">
          <!-- <span class="fadeInLeft"><span>&#9632</span> {{bookmark.title}}</span></button> -->
          <vue-typer :text='square+bookmark.title' :typeDelay='10' :repeat='0' :pre-type-delay='500' caret-animation='solid'></vue-typer>
        </button>
        </a>
      </div>
  </div>
</template>

<script>
import $ from 'jquery';
import {
  VueTyper
} from 'vue-typer';

function randomCarrot(component, text) {
  var arr = text.replace(/\s/g, '').split('');
  var char = arr[Math.floor(Math.random() * arr.length)];
  var run = true;

  var spanArray = document.getElementsByClassName('caret');

  $('.caret').each(function(){
    var caret = this;
    $(caret).addClass('display-none');

    setTimeout(function(){
      $(caret).removeClass('display-none')
    }, 500)
    window.setInterval(() => {
      caret.innerHTML = arr[Math.floor(Math.random() * arr.length)];
    },50)
  })

}


function getBookmarks() {
  var returnArray = [];
  chrome.bookmarks.getTree(function(itemTree) {
    itemTree[0].children[0].children.forEach(
      child => returnArray.push(child)
    );
  });
  return returnArray;
}

function delayAnimation() {
  document.querySelectorAll('div.fadeInLeft').forEach(function(elem, i) {
    setTimeout(function() {
      elem.classList.remove('display-none');
      elem.classList.add('animated');
    }, (i + 1) * 20);
  });
}

export default {
  data() {
    const bookmarks = getBookmarks();
    return {
      bookmarks,
      square: '■ '
    }
  },
  components: {
    VueTyper
  },
  updated: function() {
    this.$nextTick(function() {
      delayAnimation()
      randomCarrot(this, 'This is a random string for your bookmarks scrambler, Congrats!')
    });
  }
}
</script>

<style lang="css">
</style>
