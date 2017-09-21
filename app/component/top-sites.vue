<template lang="html">
  <div>
    <div class="large-border">
      <div class="small-border">
          <figure  style="height: 600px;">
            <figcaption>Top Visited Sites</figcaption>
              <div style="overflow-y: scroll; overflow-x: hidden;">
                <hr style="margin: 0; width: 98%;">
                <div style="padding: 1em 0;">
                    <div style="padding: 0" v-if="topSites" v-for="topSite in topSites" class="animated fadeIn">
                      <a v-bind:href="topSite.url" class="custom-button">
                      <button style="margin-top: 0px;" type="button" class="custom-button">
                        <span>{{square+topSite.title}}</span>
                      </button>
                      </a>
                    </div>
                </div>
                <hr style="margin: 0; width: 98%;">
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
      square: '■ '
    }
  }
}
</script>

<style>
.top-sites-panel {
  height: 600px;
}
</style>
