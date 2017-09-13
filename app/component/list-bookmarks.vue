<template lang="html">
  <div>
    <div v-if="bookmarks" v-for="bookmark in bookmarks">
      <a v-bind:href="bookmark.url" class="customButton">
      <button style="margin-top: 0px;" type="button" class="customButton">
        <span>&#9632</span> {{bookmark.title}}</button>
      </a>
    </div>
  </div>
</template>

<script>
function getBookmarks() {
  var returnArray = [];
  chrome.bookmarks.getTree(function(itemTree) {
    itemTree[0].children[0].children.forEach(
      child => returnArray.push(child)
    );
  });
  return returnArray;
}
export default {
  data() {
    const bookmarks = getBookmarks();
    return {
      bookmarks
    }
  },
}
</script>

<style lang="css">
</style>
