<template>
<div>
    <h1><center>sde电子病历编辑器</center></h1>
    <!-- 这里让编辑器居中显示 -->
    <div style="margin:0 auto;width:1000px">
        <sde-design ref='sdeDesign' width='1000px' height='610px'></sde-design>
    </div>
</div>
</template>
<script>
import sdeDesign from "./sdeDesign";
export default {
  components: {
    sdeDesign
  },
  mounted() {
    window.sde = this.$refs.sdeDesign.sde;
  }
};
</script>

<style>

</style>
