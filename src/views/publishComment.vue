<template>
  <div class="publish">
    <div class="input">
      <input type="text" v-model="comment" placeholder="请输入您的姓名">
    </div>
    <br>
    <div class="content">
      <textarea v-model="commentContent" placeholder="请输入评论"></textarea>
    </div>
    <br>
    <div class="btn">
      <button @click="publish">发布</button>
    </div>
  </div>
</template>

<script>
    export default {
        name: "publishComment",
        data() {
            return {
                id: 0,
                comment: '',
                commentContent: ''
            }
        },
        methods: {
            //发布评论
            publish() {
                this.$emit("changeComment", {
                    id: this.id++,
                    name: this.comment,
                    content: this.commentContent
                })
            }
        }
    }
</script>

<style scoped lang="less">

  .publish {
    padding: 25px;

    .input {
      width: 100%;

      input {
        width: 60%;
        height: 30px;
        border-radius: 8px;
        outline: unset;
        border: 1px solid #515a6e;
        transition: all .8s;
        padding: 8px;
        font-size: 18px;

        &:focus {
          border: 1px solid #00B7FF;
        }
      }
    }

    .content {
      textarea {
        width: 60%;
        height: 80px;
        border-radius: 8px;
        outline: unset;
        border: 1px solid #515a6e;
        transition: all .8s;
        padding: 8px;
        font-size: 18px;

        &:focus {
          border: 1px solid #00B7FF;
        }
      }
    }

    .btn {
      button {
        width: 20%;
        height: 30px;
        appearance: none;
        border-radius: 5px;
        outline: unset;
        border: 1px solid #42b983;
        background-color: #42b983;
        color: white;
        transition: all .8s;
        font-size: 14px;

        &:hover {
          opacity: 0.9;
        }
      }
    }
  }
</style>
