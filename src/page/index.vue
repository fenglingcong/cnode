<template>
  <div>
    <myHeader></myHeader>
    <div class="article_list">
      <ul>
        <li v-for="item in list" :key="item.id">
          <time v-text="$utils.changeTime(item.create_at)"></time>
          <router-link :to="'/content/' + item.id">{{item.title}}</router-link>
        </li>
      </ul>
    </div>
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
      list: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', null, res => {
        console.log(res)
        this.list = res.data
      })
    }
  }
}
</script>
