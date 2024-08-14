<template>
  <div class="card p-3">
    <div class="d-flex justify-content-between align-items-center">
      <div>
        <h3>ELS Formatter</h3>
      </div>
      <div v-if="tooltipContent.length > 0" v-tooltip="{
        content: tooltipContent,
        html: true,
        hideTriggers: ['click'],
        autoHide: true
      }" class="clickable">
        <h3>ⓘ</h3>
      </div>
    </div>
    <ElsFormatter />
  </div>
</template>

<script>
import ElsFormatter from '../ElsFormatter.vue'

export default {
  components: {
    ElsFormatter
  },
  data() {
    return {
      tooltip: {
        old: 'https://docs.google.com/spreadsheets/d/1RU6NwkdMvsKxcMbCcTkgVrzYQosqgIJtGtlYBnlJb9s/edit?gid=0#gid=0',
        guide: ''
      }
    }
  },
  computed: {
    tooltipContent() {
      return (this.tooltip.guide ? `Guide: <a href="${this.tooltip.guide}" target="_blank">Here</a><br>` : '') + (this.tooltip.old ? `Legacy: <a href="${this.tooltip.old}" target="_blank">Here</a>` : '')
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  -webkit-box-shadow: 5px 5px 15px 5px rgba(0, 0, 0, 0.3);
  box-shadow: 5px 5px 15px 5px rgba(0, 0, 0, 0.3);
}
</style>
