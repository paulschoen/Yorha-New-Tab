<template lang="html">
  <div>
      <div style="padding: 0" v-if="bookmarks" v-for="bookmark in bookmarks" class="fadeInLeft display-none">
        <a v-bind:href="bookmark.url" class="custom-button">
        <button style="margin-top: 0px;" type="button" class="custom-button">
          <!-- <span class="fadeInLeft"><span>&#9632</span> {{bookmark.title}}</span></button> -->
          <vue-typer :text='bookmark.title' :typeDelay='30' :repeat='0' :pre-type-delay='1000' caret-animation='solid'></vue-typer>
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

// function randomCarrot(component, text) {
//   var arr = text.replace(/\s/g, '').split('');
//   var char = arr[Math.floor(Math.random() * arr.length)];
//   var run = true;
//
//   var spanArray = document.getElementsByClassName('caret');
//   for (var i = 0; i < spanArray.length; i++) {
//     spanArray[i].classList.add('display-none');
//     spanArray[i].classList.remove('display-none');
//
//     window.setInterval(function(){
//       spanArray[i].innerHTML = arr[Math.floor(Math.random() * arr.length)];
//     },50)
//   }
// }


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
      bookmarks
    }
  },
  components: {
    VueTyper
  },
  updated: function() {
    this.$nextTick(function() {
      delayAnimation()
      // randomCarrot(this, 'This is a random string for your bookmarks scrambler, Congrats!')
    });
  }
}
</script>

<style lang="css">
</style>
