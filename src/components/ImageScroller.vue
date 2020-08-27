<template>
  <div class="image-scroller">
    <div class="column" v-for="(column, key) in calculatedImageArray" :key="key">
      <div class="image-container" v-for="(images, index) in column" :key="index">
        <div class="single-image-container">
          <div class="image" v-for="(singleImage, i) in images" :key="`${i}img`">
            <img :src="singleImage" alt />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      columnCount: 1,
      imagesArray: [
        'https://images.unsplash.com/photo-1598382570334-4ff525e7e4cb?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1351&q=80',
        'https://images.unsplash.com/photo-1598458697176-a0d727e317c1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1365&q=80',
        'https://images.unsplash.com/photo-1593642532009-6ba71e22f468?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598432521392-0ce5ff611c85?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=562&q=80',
        'https://images.unsplash.com/photo-1598469185215-5542684e7d29?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1349&q=80',
        'https://images.unsplash.com/photo-1598550305968-ed684e58ff47?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598533476243-9eea4c4dab3d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=658&q=80',
        'https://images.unsplash.com/photo-1598310094778-9e29b926953c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598521851537-d56abf75d325?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60',
        'https://images.unsplash.com/photo-1598520060577-e39617d6261f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1300&q=80',
        'https://images.unsplash.com/photo-1590087569917-1f93d955b1cf?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1396&q=80',
        'https://images.unsplash.com/photo-1558981001-792f6c0d5068?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598501893078-9f973deeb66c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80',
        'https://images.unsplash.com/photo-1598501709795-d5f13ba0fadd?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80',
        'https://images.unsplash.com/photo-1598474821521-ca48a956f925?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1450&q=80',
        'https://images.unsplash.com/photo-1598502751455-d9115f0e66d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=663&q=80',
        'https://images.unsplash.com/photo-1558981023-1d4b7dd8dfb9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
        'https://images.unsplash.com/photo-1598495057071-c0fe58228560?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80',
        'https://images.unsplash.com/photo-1598463073522-5aaee13b2f12?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=701&q=80',
        'https://images.unsplash.com/photo-1598491964506-0683d3f17f29?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80'
      ]
    }
  },
  computed: {
    calculatedImageArray() {
      const arr = this.imagesArray
      const arrays = []
      const arrayPartLength = Math.floor(arr.length / this.columnCount)
      const residue = arr.length % this.columnCount
      for (let i = 0; i < this.columnCount; i++) {
        let sliceAmount = ((i + 1) * arrayPartLength)
        if (i === this.columnCount - 1) {
          sliceAmount += residue
        }
        const startAmount = i * arrayPartLength
        const arrayPart = arr.slice(startAmount, sliceAmount)
        arrays.push([arrayPart, arrayPart])
      }
      console.log(arrays)
      return arrays
    }
  },
  methods: {
    calculateColumnCount() {
      const width = window.innerWidth

      if (width > 1400) {
        this.columnCount = 5
      } else if (width > 1000) {
        this.columnCount = 4
      } else if (width > 800) {
        this.columnCount = 3
      } else if (width > 600) {
        this.columnCount = 2
      } else if (width > 400) {
        this.columnCount = 1
      }
    },
    onResize() {
      this.calculateColumnCount()
    }
  },
  created() {
    this.calculateColumnCount()
    window.addEventListener('resize', this.onResize, { passive: true })
  }
}
</script>

<style lang="scss">
@mixin randomBg() {
  background-color: rgb(random(255), random(255), random(255));
}
.image-scroller {
  overflow: hidden;
  display: flex;

  :nth-child(even).column {
    .image-container {
      animation: imagetransition linear infinite reverse 100s;
    }
  }

  :nth-child(odd).column {
    .image-container {
      animation: imagetransition linear infinite 100s;
    }
  }

  .column {
    height: 100vh;
    flex: 1;

    .image-container {
      width: 100%;

      .single-image-container {
        height: 100%;
        display: flex;
        flex-direction: column;
        overflow: hidden;

        .image {
          flex: 1;
          background-size: 100%;

          img {
            width: 100%;
            display: block;
          }
        }
      }
    }
  }

  @keyframes imagetransition {
    0% {
      transform: translate3d(0, 0, 0);
    }
    100% {
      transform: translate3d(0, -100%, 0);
    }
  }
}
</style>
