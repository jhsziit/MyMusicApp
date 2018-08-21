<template>
  <div class="song-list">
    <ul>
      <li v-for="(song, index) in songs" :key="index" @click="selectItem(song, index)" class="item">
        <div class="content">
          <h2 class="name">{{song.name}}</h2>
          <p class="desc">{{getDesc(song)}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    name: "song-list",
    props: {
      songs: {
        type: Array,
        default: () => []
      }
    },
    methods: {
      selectItem(item, index) {
        this.$emit('select', item, index)
      },
      getDesc(song) {
        return `${song.singer}·${song.album}`
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '~common/scss/mixin';

  .song-list {
    .item {
      display: flex;
      align-items: center;
      box-sizing: border-box;
      height: 64px;
      font-size: $font-size-medium;
      .content {
        flex: 1;
        line-height: 20px;
        overflow: hidden;
        .name {
          @include no-wrap;
          color: $color-text;
        }
        .desc {
          margin-top: 4px;
          color: $color-text-d;
        }
      }
    }
  }
</style>
