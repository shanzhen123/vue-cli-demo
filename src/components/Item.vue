<template>
    <li class="list-group-item">
        <div class="handle">
            <el-button type="primary" class="btn-right" @click="deleteItem()" v-loading.fullscreen.lock="fullscreenLoading">删除</el-button>
        </div>
        <p class="user">
            <span>{{comment.name}}</span>说：
        </p> 
        <p class="centence">
            {{comment.content}}
        </p>
    </li>
</template>


<script>
    export default {
        props: {
            comment: Object,
            index: Number,
            delComment: Function
        },
        data() {
          return {
              fullscreenLoading: false
            }
        },
        methods: {
            deleteItem (){
                const comment = this.comment
                const delComment = this.delComment
                const index = this.index
                if(window.confirm(`确定删除${this.comment.name}的评论吗？`)){
                    this.openFullScreen(index);
                }
              },
             openFullScreen(index) {
                 this.fullscreenLoading = true;
                 setTimeout(() => {
                    this.fullscreenLoading = false;
                 }, 1000);
                 setTimeout(() => {
                    this.delComment(index);
                    this.open();
                 }, 1000);

             },
            open(){
                this.$message({
                message: '删除成功！',
                type: 'success'
             });
            }

        }
    }
</script>

<style>
li{
    transition: .5s;
    overflow: hidden;
}
.handle{
    width: 49px;
    border: 1px solid #ccc;
    background: #fff;
    position: absolute;
    right: 10px;
    top: 10px;
    text-align: center;
}
.handle a{
    display: block;
    text-decoration: none;
}
.list-group-item .centence{
    padding: 0px 50px;
}
.user{
    font-size: 22px;
}
.el-button{
    margin-left: -20px;
}
</style>
