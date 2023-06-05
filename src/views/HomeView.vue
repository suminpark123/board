<template>
  <el-table @row-click="rowClicked" :data="articles" style="width: 100%">
    <el-table-column prop="id" label="id" width="80">
    </el-table-column>
    <el-table-column prop="userId" label="userId" width="120">
    </el-table-column>
    <el-table-column prop="title" label="title">
    </el-table-column>
  </el-table>
</template>

<script>
import apiBoard from '@/api/board'




export default {
  data(){
    return{
      
      articles : null,
    }
  },
  mounted() {
    apiBoard.getArticles(0)
    .then((response)=>{
        console.log('getArticles1111', response);
        this.articles = response.data;
        
      })
      .catch((e) => {
        console.log(e);
      });
      
    // apiBoard.postArticle('userId', 'title', 'body')
    //   .then(function (response) {
    //     console.log('postArticle', response);
    //   })
    //   .catch(function (e) {
    //     console.log(e);
    //   });
    
  },
  methods :{
      rowClicked(row){
        this.$router.push({
          path:`/board/detail/${row.id}`
        })
      } 
    }
}


</script>