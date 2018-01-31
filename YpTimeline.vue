<template>
  <div class="yp-timeline">
    <slot></slot>
  </div>
</template>

<script>

export default {
  name: 'YpTimeline',
  data() {
    return {

    };
  },
};

</script>

<style lang='less' scoped >
  .yp-timeline{
    margin: 0px auto;
    padding: 30px 0px;
  }
</style>