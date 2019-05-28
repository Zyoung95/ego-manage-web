<template>
  <v-card>
      <v-flex xs12 sm10>
        <v-tree url="/item/category/list"
                :isEdit="isEdit"
                @handleAdd="handleAdd"
                @handleEdit="handleEdit"
                @handleDelete="handleDelete"
                @handleClick="handleClick"
        />
      </v-flex>
  </v-card>
</template>

<script>
  //import {treeData} from '../../mockDB'
  //import axios from '../../../node_modules/axios/dist/axios.min.js';
  import axios from 'axios'
  export default {
    name: "category",
    data() {
      return {
        treeData: [],
        isEdit:true
      }
    },
    methods: {
      handleAdd(node) {
        console.log("add .... ");
        console.log(node);
        axios({
          method: 'post',
          url: 'item/category/add',
          data: node
        }).then(({data})=>{
          //console.log(res.data)
          alert(data)
        }).catch(({data})=>{
          //console.log("哦豁")
          alert("哦豁")
        });
      },
      handleEdit(id, name) {
        console.log("edit... id: " + id + ", name: " + name);
        axios({
          method: 'put',
          url: 'item/category/update',
          params: {
            id:id,
            name:name
          }
        }).then(({data})=>{
          //console.log(res.data)
          alert(data)
        }).catch(({data})=>{
          //console.log("哦豁")
          alert("哦豁")
        });
      },
      handleDelete(id) {
        console.log("delete ... " + id);
        axios({
          method: 'delete',
          url: 'item/category/delete',
          params:{
            id:id
          }
        }).then(({data})=>{
          alert(data);
        }).catch(({data})=>{
          alert("哦豁")
        })
      },
      handleClick(node) {
        console.log(node)
      }
    }
  };
</script>

<style scoped>

</style>
