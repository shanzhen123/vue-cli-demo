<template>
  <div class="col-md-8">
    <ul class="list-group">
      <h3> 评论回复：</h3>
      <h2 v-show="comments.length === 0">暂五评论,请在评论添加!!!</h2>
      <Item v-for="(comment, index) in comments" :key="index" :comment="comment" :delComment="delComment" :index="index"/>
    </ul>
  </div>
</template>

<script>
 import Item from './Item'
    export default {
        props: ['comments','delComment'],
       components:{
          Item
       }
      }
</script>

<style>
  .reply{
    margin-top: 0px;
} 
</style>
