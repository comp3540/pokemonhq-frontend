<template>
  <div class="form-group" :class="{'has-error' : error !== ''}">
    <label class="control-label">{{label}}:</label>
    <textarea class="form-control" :rows="rows" :cols="cols" :value="value" @input="input($event.target.value)" />
    <span class="help-block" v-if="error">{{error}}</span>
  </div>
</template>
<script lang="ts">
import Vue from 'vue';
export default Vue.extend({
  props: {
    label: {
      required: true,
      type: String,
    },
    rows: {
      required: true,
      type: String,
    },
    cols: {
      required: true,
      type: String,
    },
    value: {
      required: true,
      type: String,
    },
    error: {
      type: String,
      default: '',
    },
  },
  methods: {
    input(text) {
      this.$emit('input', text);
      this.$emit('clearError');
    },
  },
});
</script>
<style type="text/css">
  textarea {
    display: block
  }
</style>
