<template>
  <div>
    <mugen-scroll
      class="dropload-down"
      v-show="showLoading"
      :handler="getData"
      :should-handle="!loading">
      <img v-show="!doneObj.done" class="loading-icon" src="../assets/img/g-loading.gif">
      <span v-show="!doneObj.done" class="text">{{ droploadDownText }}</span>
      <span v-if="doneObj.done"
        class="text"
        @click="gotoDownload">
        {{ doneObj.doneText }}
      </span>
    </mugen-scroll>
  </div>
</template>

<script>
import MugenScroll from 'vue-mugen-scroll'
import { mapGetters } from 'vuex'

export default {
  components: {
    MugenScroll
  },
  data () {
    return {
      restriction: false
      // doneObj: {}
    }
  },
  props: {
    loading: {
      type: Boolean,
      required: true
    },
    droploadDownText: {
      type: String
      // default: '正在加载中...'
    },
    done: {
      type: Boolean,
      default: false
    },
    doneText: {
      type: String,
      default: '已经加载完毕'
    },
    showLoading: {
      type: Boolean
    }
  },
  methods: {
    getData () {
      // if (this.userInfo.expireTime === -1) {
      //   this.$emit('getData')
      // } else if (this.userInfo.expireTime > Date.now()) {
      //   this.$emit('getData')
      // } else {
      // this.restriction = true
      // }
      this.restriction = true
      // this.$emit('getData')
    },
    gotoDownload () {
      window.location.href = 'https://a.app.qq.com/o/simple.jsp?pkgname=com.gohoc.afinancegeek'
    }
  },
  computed: {
    ...mapGetters(['userInfo']),
    doneObj () {
      if (this.restriction) {
        return {
          done: true,
          doneText: '下载飞笛智投app，查看更多资讯'
        }
      }
      return {
        done: this.done,
        doneText: this.doneText
      }
    }
  }
}
</script>

<style scoped>
.dropload-down {
  height: 50px;
  line-height: 50px;
  text-align: center;
  color: #4694f4;
}
.dropload-down .loading-icon {
  width: 30px;
  height: 30px;
  vertical-align: middle;
  padding-right: 4px;
}
.text {
  vertical-align: middle;
  text-decoration: underline;
  font-size: 14px;
}
</style>
