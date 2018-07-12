<template>
  <div>
    <myHeader></myHeader>
    <h2 v-text="info.title"></h2>
    <p v-if="info.author">作者：{{info.author.loginname}}   {{$utils.changeTime(info.create_at)}}</p>
    <hr>
    <article v-html="info.content"></article>
    <h3>网友回复：</h3>
    <ul>
      <li v-for="item in info.replies" :key="item.id">
        <p>评论者：{{item.author.loginname}}  评论于：{{$utils.changeTime(item.create_at)}}</p>
        <article v-html="item.content"></article>
      </li>
    </ul>
    <myFooter></myFooter>
  </div>
</template>
<script>
import myHeader from '../components/header.vue'
import myFooter from '../components/footer.vue'
export default {
  components: {myHeader, myFooter},
  data () {
    return {
      id: this.$route.params.id,
      info: {}
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topic/' + this.id, null, res => {
        console.log(res)
        this.info = res.data
      })
    }
  }
}
</script>
