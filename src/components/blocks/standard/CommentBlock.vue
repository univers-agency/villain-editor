<template>
  <Block
    :block="block"
    :parent="parent"
    @add="$emit('add', $event)"
    @move="$emit('move', $event)"
    @delete="$emit('delete', $event)">
    <div class="villain-block-description">
      Kommentar (vises ikke)
    </div>
    <div class="villain-block-comment">
      <code><pre>{{ block.data.text }}</pre></code>
    </div>
    <template slot="config">
      <div class="form-group">
        <label>Kommentar</label>
        <textarea
          ref="txt"
          v-model="block.data.text"
          class="form-control text-mono"></textarea>
      </div>
    </template>
  </Block>
</template>

<script>
import Block from '@/components/blocks/system/Block'

export default {
  name: 'CommentBlock',

  components: {
    Block
  },

  props: {
    block: {
      type: Object,
      default: () => {}
    },

    parent: {
      type: String,
      default: null
    }
  },

  inject: [
    'available'
  ],

  data () {
    return {
      uid: null
    }
  },

  created () {
    console.debug('<CommentBlock /> created')
  }
}
</script>
