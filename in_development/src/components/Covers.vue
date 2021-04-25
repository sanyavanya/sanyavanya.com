<template>
  <div>
    <div class="coversContainer">
      <div class="covers" :style="{transform: 'translate3d(' + horizontalContainerShift + 'px, 0px, 0px'}">
        <template v-for="(cover, index) in covers" v-bind:key="cover.title">
          <Cover
            :cover="cover"
            :index="index"
            :zoomedCoverIndex="zoomedCoverIndex"
            @click="zoomClicked(index)"
          ></Cover>
        </template>        
      </div>      
    </div>
  </div>
</template>
<script>
  import Cover from './Cover.vue'
  export default {
    name: 'Covers',
    components: { Cover },
    data() {
      return {
          covers: [
              {
                title: 'Follin',
                image: 'https://upload.wikimedia.org/wikipedia/en/thumb/e/ed/Green_Day_-_American_Idiot_album_cover.png/220px-Green_Day_-_American_Idiot_album_cover.png'
              },
              {
                title: 'Another',
                image: 'https://upload.wikimedia.org/wikipedia/en/8/88/Periphery_IV_Hail_Stan.jpg'
              },
              {
                title: 'Three',
                image: 'https://i.pinimg.com/originals/3a/f0/e5/3af0e55ea66ea69e35145fb108b4a636.jpg'
              },
              {
                title: 'Bitchin',
                image: 'https://99designs-blog.imgix.net/blog/wp-content/uploads/2018/09/attachment_67353774.png?auto=format&q=60&fit=max&w=930'
              },
              {
                title: 'Flock',
                image: 'https://images.squarespace-cdn.com/content/v1/53b6eb62e4b06e0feb2d8e86/1607362705516-R5Q22H4FVIVPNMW8OWD7/ke17ZwdGBToddI8pDm48kOM0wi0zWgY49OChaGdbQod7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z5QPOohDIaIeljMHgDF5CVlOqpeNLcJ80NK65_fV7S1Udq808UFTE3RUCYZpscC1JaI0xjbDb9OOCsv-L8MD1ND_7k-9-XsFQ9lvpTgv0wwCA/SamSpratt_KidCudi_ManOnTheMoon3_AlbumCover_Web.jpg?format=original'
              },
              {
                title: 'Jackson',
                image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRqwr9ZzXNfzy0Zpz5kzUI_JxyuE06J2ps2Sw&usqp=CAU'
              }
          ],
          zoomedCoverIndex: 0
      }
    },
    methods: {
      zoomClicked: function(index) {
        this.zoomedCoverIndex = index
      }
    },
    computed: {
      horizontalContainerShift() {
        let smallCoverSize = 100 //sync with scss! And also, make it all responsive!
        if (this.covers.length % 2 === 0) return (0.5 * this.covers.length * smallCoverSize - 0.5 * smallCoverSize) - this.zoomedCoverIndex * smallCoverSize;
        return (Math.floor(this.covers.length/2) * smallCoverSize) - this.zoomedCoverIndex * smallCoverSize;
      }
    }
  }
</script>

<style lang="scss" scoped>
  .coversContainer {
    display: flex;
    justify-content: center;
  }
  .covers {
    border: 1px solid red;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    transition-duration: 500ms;
  }
</style>