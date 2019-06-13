<script>
function importAll(r) {
  let images = {};
  r.keys().map(function(item) {
    images[item.replace("./", "")] = r(item);
    return null;
  });
  //console.log(images);
  return images;
}

function getImgs() {
  return importAll(require.context("../assets/images", true, /\.jpg$/));
}

export default {
  name: "CarouselComponent",
  data() {
    return {
      images: getImgs()
    };
  }
};
</script>

<template>
  <div class="row">
    <div class="col-md-12">
      <div class="carousel">
        <carousel :per-page="1" :navigation-enabled="true">
          <slide v-for="(img,k,i) in images" :key="i">
            <img height="300" :src="img" alt="img">
          </slide>
        </carousel>
      </div>
    </div>
  </div>
</template>

<style scoped>
.carousel {
  width: 80%;

  margin: 0 auto;
}
</style>
