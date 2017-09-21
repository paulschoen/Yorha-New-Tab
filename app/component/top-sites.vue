<template lang="html">
  <div class="large-border">
    <div class="small-border">
      <div class="top-sites-panel">
        <figure>
          <figcaption>Top Visited Sites</figcaption>
          <div v-if="topSites" v-for="topSite in topSites">
            <a v-bind:href="topSite.url" class="custom-button">
            <button style="margin-top: 0px;" type="button" class="custom-button">
              <span>&#9632</span> {{topSite.title}}</button>
            </a>
          </div>
        </figure>
      </div>
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
  height: 600px;
}
</style>
