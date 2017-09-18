<template lang="html">
  <div class="top-sites-panel">
    <div v-if="topSites" v-for="topSite in topSites">
      <a v-bind:href="topSite.url" class="custom-button">
      <button style="margin-top: 0px;" type="button" class="custom-button">
        <span>&#9632</span> {{topSite.title}}</button>
      </a>
    </div>
  </div>
</template>

<script>
  function gettopSites() {
    var returnArray = [];
    chrome.topSites.get(function(topSitesArr) {
      topSitesArr.forEach((site) => returnArray.push(site))
    });
    return returnArray;
  }
  export default {
    data() {
      const topSites = gettopSites();
      return {
        topSites: topSites,
      }
    }
  }
</script>

<style>
  .top-sites-panel {
    height: auto;
    background-color: #dcd8c0;
  }
</style>
