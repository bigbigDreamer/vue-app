<template>
  <div id="app">
    <div>
      <h1>谈谈你对Vue学习的看法吧</h1>
    </div>
    <div class="commentZone">
      <div class="left">
        <publish-comment @changeComment="changeComment"/>
      </div>
      <div class="right">
        <p v-if="hasComment">暂无人评论,来谈谈你的看法叭</p>
        <comment-list :commentList="commentList" @delComment="delComment"/>
      </div>
    </div>
  </div>
</template>

<script>
    import PublishComment from './views/publishComment'
    import commentList from './views/commentList'

    export default {
        name: 'App',
        components: {
            PublishComment,
            commentList
        },
        data() {
            return {
                //评论列表
                commentList: [],
                //判断那时候付
                hasComment:true
            }
        },
        methods: {
            //发布评论之后，改变评论数组
            changeComment(val) {
                // console.log(val);
                this.commentList.push(val)
            },
            //删除评论
            delComment(val) {
                this.commentList.forEach((item, index) => {
                    if (item.id === val) {
                        this.commentList.splice(index, 1)
                    }
                })
            }
        },
        watch: {
            commentList: function (val) {
                console.log(val)
                if(val.length) {
                    this.hasComment = false;
                }
            }
        }
    }
</script>

<style lang="less">
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    height: 200px;

    .commentZone {
      display: flex;
      flex-flow: wrap;

      .left {
        flex: 1;
        flex-basis: 600px;
        margin: 0 auto;
      }

      .right {
        flex: 1;
        flex-basis: 400px;
        margin: 0 auto;

        p {
          font-size: 18px ;
          text-decoration-line: underline;
        }
      }
    }
  }

</style>
