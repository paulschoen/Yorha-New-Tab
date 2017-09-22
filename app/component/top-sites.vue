<template lang="html">
  <div>
    <div class="large-border">
      <div class="small-border">
          <figure  style="height: 600px; padding-left: 0px !important;">
            <figcaption style="margin-left:0px !important;">Top Visited Sites</figcaption>
              <div class="inside-panel-container">
                <hr class="button-panel-line">
                <div class="inside-panel-offset">
                    <div style="padding: 0" v-if="topSites" v-for="topSite in topSites" class="animated fadeIn">
                      <a v-bind:href="topSite.url" class="custom-button">
                      <button type="button" class="custom-button inside-panel-button">
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
