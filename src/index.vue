<template>
  <view class="container">
    <Navigation />
  </view>
</template>
<script>
import Navigation from './navigation';
import Vue from "vue-native-core";
import{ VueNativeBase } from "native-base";
import store from './store';
import ScreenWithDrawer from './components/ScreenWithDrawer';

Vue.use(VueNativeBase);
Vue.component('ScreenWithDrawer', ScreenWithDrawer);
Vue.prototype.$store = store;
export default {
  components: {
    Navigation
  }
}
</script>
<style>
.container {
  flex: 1;
}
</style>