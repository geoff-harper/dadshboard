<template>
  <tbody class="stock-row-group">
    <tr v-for="(variation, i) in type.variations" :class="[i === 0 ? 'stock-row--title' : null, 'stock-row']">
      <td>{{ i === 0 ? type.name : null }}</td>
      <td>{{ variation.size }}</td>
      <td class="number-row">{{ variation.quantity }}</td>
      <td>
        <button
          class="stock-row__remove-button"
          @click="$emit('delete', [type.id, i])">&times;</button>
      </td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: 'FreezerStockRow',
  props: {
    type: {
      type: Object,
      required: true
    }
  },
  data () {
    return {}
  }
}
</script>

<style>

</style>
