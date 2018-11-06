<template>
  <div>
    <div>
        <header class="site-header jumbotron">
            <div class="container">
                <div class="col-xs-12">
                    <h1>请发表vue言论</h1>
                </div>
            </div>
            
        </header>
        <div class="container">
            <Form :addComment="addComment"/> 
            <List :comments="comments" :delComment="delComment"/>
        </div>
    </div>
  </div>
</template>

<script>
  import Form from './components/Add.vue'
  import List from './components/List.vue'
export default {
    data() {
        return {
            comments: [ // 数据在哪个组件，更新数据的方法就应该在哪个组建里面
                {
                    name: "BOB",
                    content: "听说Golang很牛p"
                },
                {
                    name: "TOM",
                    content: "JS才是web王道"
                },
                {
                    name: "FACKER",
                    content: "我大PHP是最牛掰的"
                }
            ]
      
        }
    },
    methods: {
        addComment (comment) {
            this.comments.unshift(comment)
        },
        delComment (index){
            this.comments.splice(index,1)
        }
    },
    components: {
      Form,
      List
  }
}

</script>


