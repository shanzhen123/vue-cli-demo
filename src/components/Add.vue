<template>
  <div class="col-md-4">
        <form class="form-horizontal">
            <div class="form-group">
                <label>用户名</label>
                <input type="text" name="" class="form-control" placeholder="请输入用户名" v-model="name" />
            </div>
            <div class="form-group">
                <label>请输入评论：</label>
                <textarea class="form-control" rows="6" placeholder="请输入评论内容" v-model="content"></textarea>
            </div>
            <div class="form-group">
                <div class="col-sm-offset-2 col-sm-10">
                    <button type="button" class="btn btn-default btn-right" @click="openFullScreen"  v-loading.fullscreen.lock="fullscreenLoading">提交</button>
                </div>
            </div>
        </form>
    </div>
</template>


<script>
    export default {
        props: {
            addComment: {
                type: Function,
                required: true
            }
        },
        data(){
           return {
               name: "",
               content: "",
               fullscreenLoading: false
            }
        },
        methods:{
            add(){
                //1 坚持输入的数据合法性
                const name = this.name.trim();
                const content = this.content.trim();
                if (!name || !content){
                    alert("姓名或内容不能为空！");
                    return
                }
                //2 根据输入的数据，封装成一个comment对象
                const comment = {
                    name,
                    content
                }
                //3 添加到comments中
                this.addComment(comment)
                //4 清除输入框的内容
                this.name = ""
                this.content= ""
            },
             openFullScreen() {
                 this.fullscreenLoading = true;
                 setTimeout(() => {
                    this.fullscreenLoading = false;
                 }, 1000);
                setTimeout(() => {
                 this.add();
                }, 1200);
             }
        }
    }
</script>


<style>
</style>
