<template>
  <mu-carousel>
    <mu-carousel-item>
      <img :src="IMG1" />
    </mu-carousel-item>
    <mu-carousel-item>
      <img :src="IMG2" />
    </mu-carousel-item>
  </mu-carousel>
</template>
<script>
import IMG1 from "@/assets/carousel1.jpg";
import IMG2 from "@/assets/carousel2.jpg";
export default {
  name: "Carousel",
  data() {
    return {
      IMG1,
      IMG2
    };
  }
};
</script>