<template>
  <v-container>
    <PhotoForm v-if="photos.length < 11" @addPhoto="addPhoto" />
    <div v-else>Вы не можете добавить больше фото</div>
    <v-row>
      <Photo v-for="photo in $store.getters.getAllPhotos" :key="photo.id" :photo="photo" />
    </v-row>
    <PhotoDialog />
  </v-container>
</template>

<script>
import Photo from '@/components/photo/Photo'
import PhotoDialog from '@/components/photo/PhotoDialog.vue';
import PhotoForm from '@/components/photo/PhotoForm.vue';

  export default {
    components: { Photo, PhotoForm, PhotoDialog },
    data: () => ({
      photos: [],
      // currentPhoto: {},
      // dialogVisible: false,
    }),
    mounted() {
      // this.fetchTodo()
      this.$store.dispatch('fetchPhotos')
    },
    methods: {
      // fetchTodo() {
      //   this.axios.get('https://jsonplaceholder.typicode.com/photos?_limit=10')
      //     .then(response => this.photos = response.data)
      // },
      addPhoto(photo) {
        this.photos.push(photo);
      },
      openPhoto(photo) {
        this.currentPhoto = photo
        this.dialogVisible = true
      },
    }
  }
</script>

<style scoped>

</style>