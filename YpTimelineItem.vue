<template>
  <div class="yp-timeline-box">
    <div>
      <div
        v-if="position === 'left'"
        :class="['yp-timeline-card', { 'yp-timeline-card-reverse': reverse }]"
      >
        <slot name="title">
        </slot>
        <div class="timeline-card-content">
          <slot></slot>
        </div>
        <div class="time-line-card-arrow">
          <div
            class="timeline-mark"
            :style="{
              'backgroundColor' : markColor,
              'boxShadow' : `0px 0px 2px 2px ${markShadowColor}`,
            }"
          ></div>
        </div>
      </div>
    </div>
    <div>
      <div
        v-if="position === 'right'"
        :class="['yp-timeline-card', { 'yp-timeline-card-reverse': reverse }]"
      >
        <slot name="title">
        </slot>
        <div class="timeline-card-content">
          <slot></slot>
        </div>
        <div class="time-line-card-arrow-v">
          <div
            class="timeline-mark"
            :style="{
              'backgroundColor' : markColor,
              'boxShadow' : `0px 0px 2px 2px ${markShadowColor}`,
            }"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {

    };
  },
  props: {
    position: {
      type: String,
      default: 'left',
    },
    markColor: {
      type: String,
      default: '#ffc629',
    },
    markShadowColor: {
      type: String,
      default: '#cccccc',
    },
    reverse: {
      type: Boolean,
      default: false,
    },
  },
};

</script>

<style lang='less' scoped >
.yp-timeline-box{
  display: flex;
  >div{
    flex: 1;
    position: relative;
    padding: 10px 15px;
    .yp-timeline-card{
      background-color: #ffffff;
      padding: 15px;
      position: relative;
      border: 1px solid #cccccc;
      @arrow-border-width: 10px;
      border-radius: 5px;
      .timeline-card-content{
        padding: 5px 0px;
        text-indent: 12px;
        width: 100%;
        word-break: break-all;
      }
      .time-line-card-arrow, .time-line-card-arrow-v{
        content: '';
        position: absolute;
        width: 0;
        height: 0;
        border-width: @arrow-border-width;
        border-style: solid;
        &:after{
          content: '';
          position: absolute;
          width: 0;
          height: 0;
          border-width: @arrow-border-width - 2;
          border-right-width: @arrow-border-width - 1;
          border-left-width: @arrow-border-width - 1;
          border-style: solid;
        }
        .timeline-mark{
          content: '';
          position: absolute;
          width: 14px;
          height: 14px;
          border-radius: 15px;
          z-index: 3;
        }
      }
      .time-line-card-arrow{
        right: -20px;
        top: 1px;
        border-color: transparent transparent transparent #cccccc;
        &:after{
          border-color: transparent transparent transparent #ffffff;
          left: -@arrow-border-width;
          top: -@arrow-border-width + 2;
        }
        .timeline-mark{
          top: -4px;
          right: -@arrow-border-width * 1.4;
        }
      }
      .time-line-card-arrow-v{
        left: -20px;
        top: 1px;
        border-color: transparent #cccccc transparent transparent;
        &:after{
          border-width: @arrow-border-width - 2;
          border-right-width: @arrow-border-width - 1;
          border-left-width: @arrow-border-width - 1;
          border-style: solid;
          border-color: transparent #ffffff transparent transparent;
          right: -@arrow-border-width;
          top: -@arrow-border-width + 2;
        }
        .timeline-mark{
          top: -4px;
          left: -@arrow-border-width * 1.4;
        }
      }
    }
    .yp-timeline-card-reverse{
      background-color: #3a3c48;
      .time-line-card-arrow{
        &:after{
          border-color: transparent transparent transparent #3a3c48;
        }
      }
      .time-line-card-arrow-v{
        &:after{
          border-color: transparent #3a3c48 transparent transparent;
        }
      }
    }
  }
  @tree-size: 1px;
  @tree-color: #999999;
  >div:first-child{
    border-right: @tree-size solid @tree-color;
  }
  >div:last-child{
    border-left: @tree-size solid @tree-color;
  }
}
</style>