<template>
  <textarea
    ref="area"
    name="twit-board"
    columns="30"
    class="twit-board"
    maxlength="140"
    @input="$emit('update:modelValue', modelValue)"
    @focus="$emit('update:focus', position)"
    v-model="modelValue"
  ></textarea>
</template>

<script>

export default {
  props: {
    modelValue: String,
    position: Number
  },

  methods:{
    focusArea() {
      this.$refs.area.focus()
    }
  },
  emits: ['update:modelValue', "update:isFocused"],
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