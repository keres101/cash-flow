<script setup>
import { toRefs, computed } from 'vue'

const props = defineProps(['title', 'id', 'description', 'amount'])
const emit = defineEmits(['remove'])

const { title, id, description, amount } = toRefs(props)

const remove = () => {
  emit('remove', id.value)
}

const currencyFormatter = new Intl.NumberFormat('es-PE', {
  style: 'currency',
  currency: 'PEN',
})

const amountCurrency = computed(() => {
  return currencyFormatter.format(amount.value)
})

const isNegative = computed(() => amount.value < 0)
</script>
<template>
  <div class="movement">
    <div>
      <h4>{{ title }}</h4>
      <p>{{ description }}</p>
    </div>
    <div>
      <div class="action">
        <img src="../../assets/trash.svg" alt="delete" @click="remove" />
        <p :class="{ red: isNegative, green: !isNegative }">
          {{ amountCurrency }}
        </p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}
.movement .action img {
  margin-bottom: 16px;
}
.red {
  color: red;
}
.green {
  color: green;
}
</style>
