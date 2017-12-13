<template>
  <tr :class="['stock-input-row', hasError ? 'error' : '']">
    <td>
      <input
        v-model="newNameText"
        @click="newNameText = ''"
        class="stock-input-row__field"
        type="text"
        placeholder="">
    </td>
    <td>
      <select
        v-model="newSizeOption"
        class="stock-input-row__field">
        <option value="" disabled hidden>Select a size</option>
        <option value="Large">Large</option>
        <option value="Medium">Medium</option>
        <option value="Small">Small</option>
      </select>
    </td>
    <td>
      <input
        v-model.number="newQuantityNum"
        @click="newQuantityNum = ''"
        class="stock-input-row__field"
        type="text"
        placeholder="">
    </td>
    <td><button @click="emitStock" class="stock-add">&plus;</button></td>
  </tr>
</template>

<script>
export default {
  data () {
    return {
      newNameText: '',
      newSizeOption: '',
      newQuantityNum: '',
      hasError: false
    }
  },
  methods: {
    emitStock () {
      const bool = this.newNameText !== '' &&
        this.newSizeOption !== '' &&
        this.newQuantityNum !== null &&
        typeof this.newQuantityNum === 'number'
      if (bool) {
        const data = {
          newNameText: this.newNameText,
          newSizeOption: this.newSizeOption,
          newQuantityNum: this.newQuantityNum
        }
        this.$emit('add', data)
        this.newNameText = ''
        this.newSizeOption = ''
        this.newQuantityNum = ''
        this.hasError = false
      } else {
        this.hasError = true
      }
    }
  }
}
</script>

<style>

</style>
