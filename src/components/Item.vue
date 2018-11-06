<template>
    <li class="list-group-item">
        <div class="handle">
            <a-button @click="deleteItem()">删除</a-button>
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
        methods: {
            deleteItem (){
                const comment = this.comment
                const delComment = this.delComment
                const index = this.index
                if(window.confirm(`确定删除${this.comment.name}的评论吗？`)){
                    delComment(index)
                    success()
                }
              }
        },
        success () {
          this.$message.success("删除成功!");
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
</style>
