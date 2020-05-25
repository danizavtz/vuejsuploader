<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!-- to a file upload to work with the form must be a multipart form-data, it is setted in axios-->
    <form action="." method="post" @submit.prevent="handleSubmit" enctype="multipart/form-data">
      <label for="nome">Nome </label>
      <input id="nome" type="text" v-model="nome" name="nome"><br>
      <input id="image" type="file" name="image" ref="file" @change="handleFileUpload()"/><br>
      <input id="btnsubmit" type="submit" value="enviar">
    </form>
  </div>
</template>

<script>
import apiendpoint from '@/services/backend.js'
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  data() {
    return {
      nome: '',
      file: ''
    }
  },
  methods: {
    handleSubmit() {
      const formData = new FormData();
      formData.append('image', this.file);
      formData.append('nome', this.nome);
      apiendpoint.post('/uploadfile', formData, {
        headers: {
              'Content-Type': 'multipart/form-data'
            }
      }).then(function(response) {
        console.log(response.data)
      }).catch(function(response) {
        console.log(response.data)
      })
    },
    handleFileUpload() {
      this.file = this.$refs.file.files[0];
    }
  }
}
</script>
