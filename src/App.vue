<template>
  <div id="app">
    <headerDiv></headerDiv>
    <transition name="fade">
      <router-view id="container" class="mh-box"></router-view>
    </transition>
    <!--<go-home></go-home>-->
    <downloadFoot></downloadFoot>
    <loading></loading>
  </div>
</template>

<script>
import HeaderDiv from './components/Header'
// import GoHome from './components/GoHome'
import Loading from './components/Loading'
import downloadFoot from './components/app/downloadFoot'

export default {
  name: 'app',
  components: {
    HeaderDiv,
    // GoHome,
    Loading,
    downloadFoot
  },
  data () {
    return {

    }
  }
}
</script>

<style>
#app{
  padding-top: 1.07rem;
}
.details-content-s p img{
  width: 9rem;
  text-indent: 0;
  margin-left: -0.91rem;
}
.details-content-s p{
  text-indent: 0.91rem;
  margin-bottom: 0.53rem;
}

.mh-box{
  min-height: 94vh;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .4s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0
}


/*body #nprogress .bar {
background: #f4ce46;
}
body #nprogress .peg {
box-shadow: 0 0 10px #f4ce46, 0 0 5px #f4ce46;
}*/
</style>
