<template>
  <form :class="['stock-input-form', hasError ? 'error' : '']">
    <label class="field-container">
      Name
      <input
        v-model="newNameText"
        @click="newNameText = ''"
        class="stock-input-row__field field"
        type="text"
        placeholder="">
    </label>
    <label class="field-container">
      Size
      <select
        v-model="newSizeOption"
        class="stock-input-row__field field">
        <option value="" disabled hidden></option>
        <option value="Large">Large</option>
        <option value="Medium">Medium</option>
        <option value="Small">Small</option>
      </select>
    </label>
    <label class="field-container">
      Quantity
      <input
        v-model.number="newQuantityNum"
        @click="newQuantityNum = ''"
        class="stock-input-row__field field"
        type="text"
        placeholder="">
    </label>
    <button @click="emitStock" class="stock-add button">&plus;</button>
  </form>
</template>

<script>
export default {
  name: 'FreezerStockInput',
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

<style lang="scss">
  @import '~vars';
  @import '~mixins';
  .stock-input-form {
    padding-top: 20px;
    
    .field-container {
      flex: unset;
    }
    
    .field {
      margin-bottom: 10px;
    }
  }
  
  @include bp(md) {
    .stock-input-form {
      display: flex;
      flex-flow: row nowrap;
      align-items: stretch;
      width: 100%;
      
      .field-container {
        flex: 1 0 auto;;
      }

      .field {
        flex: 1 0 20%;
        margin-bottom: 0px;
      }
    }
  }
</style>
