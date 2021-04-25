<template>
  <div>
    <!-- <img :src="cover.image" class="cover" :class="decorationClass"> -->
    <div class="cover"  :class="decorationClass" :style="{backgroundImage: `url(${cover.image})`}"></div>
  </div>
</template>

<script>
  // import { mapGetters } from 'vuex'
  export default {
    name: 'Cover',
    props: ['cover', 'index', 'zoomedCoverIndex'],
    computed: {
      decorationClass() {
        if (this.index === this.zoomedCoverIndex) return 'zoom'
        if (this.index === this.zoomedCoverIndex - 1) return 'shadowRight'
        if (this.index === this.zoomedCoverIndex + 1) return 'shadowLeft'
        return null
      }
      // ...mapGetters([
      //   'covers'
      // ])
    }
  }
</script>

<style lang="scss" scoped>

  .zoom {
    transition-duration: 400ms !important;
    transform: scale(1.2);
    opacity: 1 !important;
    z-index: 2 !important;
  }

  .shadowLeft {
    box-shadow: inset 50px 0 50px rgba(0, 0, 0, 0.5);
  }

  .shadowRight {
    box-shadow: inset -50px 0 50px rgba(0, 0, 0, 0.5);
  }

  .cover {
    z-index: 1;
    width: 100px;
    height: 100px;
    position: relative;
    background-size: cover;
    transition-duration: 150ms;
    opacity: 0.8;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;
    font-size: 20pt;
    font-family: "Courier New";
    font-weight: bold;
    font-size: 20pt;

    &:hover {
      cursor: pointer;
    }
  }
</style>