<template>
  <textarea
    name="twit-board"
    columns="30"
    class="twit-board"
    maxlength="140"
    v-on:input="$emit('update:modelValue', modelValue)"
    v-model="modelValue"
  ></textarea>
</template>

<script>

export default {
  props: {
    modelValue: String
  },
  emits: ['update:modelValue'],
}

</script>

<style scoped>
a {
  color: #42b983;
}

textarea {
  display: block;
}
</style>