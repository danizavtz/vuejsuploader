<template>
  <div>
      <p v-for="item in lista" :key="item.id" >
          {{ item.nome }}
          <img :src="`http://localhost/${item.currentpath}.${item.extension}`">
      </p>
  </div>
</template>

<script>
import apiendpoint from '@/services/backend.js'

export default {
  name: 'Listar',
  created(){
      this.loadFilesInfo()
  },
  data: function() {
      return {
          lista : []
      }
  },
  methods: {
      async loadFilesInfo(){
          try {
              const { data } = await apiendpoint.get('/files')
              this.lista = data
          } catch (err) {
              console.log(err)
          }
      }
  }
}
</script>