<template>
  <div class="container">
    <div class="image-container" v-for="(images, index) in getDoubleArray" :key="index">
      <div class="single-image-container">
        <div class="image"  v-for="(singleImage, i) in images" :key="`${i}img`">
          <img :src="singleImage" alt />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imagesArray: [
        'https://images.unsplash.com/photo-1598382570334-4ff525e7e4cb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1351&q=80',
        'https://images.unsplash.com/photo-1598458697176-a0d727e317c1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1365&q=80',
        'https://images.unsplash.com/photo-1593642532009-6ba71e22f468?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598432521392-0ce5ff611c85?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=562&q=80'
      ]
    }
  },
  computed: {
    getDoubleArray() {
      const arr = this.imagesArray
      return [
        arr,
        arr
      ]
    }
  }
}
</script>

<style lang="scss">
@mixin randomBg() {
  background-color: rgb(random(255), random(255), random(255));
}

.container {
  height: 100vh;
  overflow: hidden;

  .image-container {
    height: 200%;
    // animation: imagetransition linear infinite 5s;

    .single-image-container {
      height: 100%;
      display: flex;
      flex-direction: column;
      overflow: hidden;

      .image {
        img {
          height: 100%;
        }
      }
    }
  }
}

@keyframes imagetransition {
  0% {
    transform: translateY(0%);
  }
  100% {
    transform: translateY(-100%);
  }
}
</style>
