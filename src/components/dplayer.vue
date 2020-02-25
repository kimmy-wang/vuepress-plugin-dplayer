<template>
  <div ref="dplayer"></div>
</template>

<script>
export default {
  name: 'DPlayer',
  props: {
    options: Object,
  },
  mounted() {
    import('dplayer').then(({ default: DPlayer }) => {
      const root = this.$refs.dplayer
      this.dp = new DPlayer({
        container: root,
        ...this.options,
      })
    })
  },
  beforeDestroy() {
    this.dp && this.dp.pause()
  },
  methods: {},
}
</script>

<style scoped>
@import '~dplayer/dist/DPlayer.min.css';
</style>
