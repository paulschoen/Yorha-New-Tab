<template lang="html">
  <div>
      <div style="padding: 0" v-if="bookmarks" v-for="bookmark in bookmarks" class="fadeInLeft display-none">
        <a v-bind:href="bookmark.url" class="custom-button">
        <button style="margin-top: 0px;" type="button" class="custom-button">
          <span>&#9632</span> {{bookmark.title}}</button>
        </a>
      </div>
  </div>
</template>

<script>
import $ from 'jquery';

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
  document.querySelectorAll('div.fadeInLeft').forEach(function(elem, i){
    setTimeout(function(){
      elem.classList.remove('display-none')
      elem.classList.add('animated');
     }, (i+1) * 20);
  });
}

export default {
  data() {
    const bookmarks = getBookmarks();
    return {
      bookmarks
    }
  },
  updated: function () {
    this.$nextTick(function() {
      delayAnimation()
    });
  }
}
</script>

<style lang="css">
</style>
