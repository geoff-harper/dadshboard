<template>
  <section id="freezer" class="card card--small-view">
    <h1 class="card__title">Freezer Stock</h1>
    <table class="stock-table">
      <thead>
        <th>Name</th>
        <th>Size</th>
        <th class="number-row">Quantity</th>
        <th></th>
      </thead>
      <FreezerStockRow
        v-for="type in stock"
        :key="type.id"
        @delete="deleteVariation"
        :type="type"></FreezerStockRow>      
    </table>
    <FreezerStockInput @add="addVariation"></FreezerStockInput>
  </section>
</template>

<script>
import FreezerStockRow from './FreezerStockRow'
import FreezerStockInput from './FreezerStockInput'

let itemCounter = 0

export default {
  name: 'FreezerStock',
  components: {
    FreezerStockRow,
    FreezerStockInput
  },
  methods: {
    addVariation ({newNameText, newSizeOption, newQuantityNum}) {
      for (let type of this.stock) {
        if (type.name === newNameText) {
          type.variations.push({
            size: newSizeOption,
            quantity: newQuantityNum
          })
          return
        }
      }
      this.stock.push({
        id: ++itemCounter,
        name: newNameText,
        variations: [
          {
            size: newSizeOption,
            quantity: newQuantityNum
          }
        ]
      })
    },
    deleteVariation ([typeId, variationId]) {
      for (let type of this.stock) {
        if (type.id === typeId) {
          type.variations = type.variations.filter((variation, i) => {
            return i !== variationId
          })
          return
        }
      }
    }
  },
  data () {
    return {
      stock: [
        {
          id: ++itemCounter,
          name: 'Porkchop',
          variations: [
            {
              size: 'Large',
              quantity: 2
            },
            {
              size: 'Medium',
              quantity: 2
            }
          ]
        },
        {
          id: ++itemCounter,
          name: 'Boeuf',
          variations: [
            {
              size: 'Medium',
              quantity: 1
            },
            {
              size: 'Small',
              quantity: 3
            }
          ]
        }
      ]
    }
  }
}
</script>

<style lang="scss">
  #freezer {
    overflow: hidden;
  }
  .stock-table th {
    padding-bottom: 0px;
  }
</style>
