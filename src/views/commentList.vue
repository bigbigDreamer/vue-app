<template>
  <div class="commentList">
    <ul>
      <li v-for="(item,index) in commentList" :key="index">
            <span>
              {{item.name}} 说：
            </span>
        <span class="del">
          <button @click="del(item.id)">删除</button>
        </span>
        <br>
        <p>
          {{item.content}}
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
    export default {
        name: "commentList",
        data() {
            return {}
        },
        props: {
            commentList: {
                type: Array,
                default() {
                    return [
                        {
                            id:0,
                            name: '张三',
                            content: '我太难了~~~',
                        }
                    ]
                }
            }
        },
        methods: {
            del(id) {
                this.$emit("delComment",id);
            }
        }
    }
</script>

<style scoped lang="less">
  .commentList {
    ul {
      list-style: none;

      li {
        text-align: left;
        width: 80%;
        height: 100px;
        border: 1px solid #515a6e;
        padding: 18px;
        box-sizing: border-box;
        border-radius: 18px;
        margin-bottom: 18px;
        display: flow-root;

        span {
          &:first-child {
            font-size: 20px;
          }

          /*&:last-child {*/
          /*  font-size: 18px;*/
          /*  text-indent: 5em;*/
          /*}*/
        }
        .del {
          button {
            float: right;
            width: 15%;
            height: 25px;
            appearance: none;
            border-radius: 5px;
            outline: unset;
            border: 1px solid #ed4014;
            background-color: #ed4014;
            color: white;
            transition: all .8s;
            font-size: 14px;
            &:hover {
              opacity: 0.9;
            }
          }
        }

        p {
          font-size: 18px;
          text-indent: 2em;
        }
      }
    }

  }
</style>
