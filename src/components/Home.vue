<script setup>
import Layout from './Layout.vue'
import Header from './Header.vue'
import Resume from './Resume/Index.vue'
import Movements from './Movements/Index.vue'
import Action from './Action.vue'

const movements = [
  {
    id: 1,
    title: 'Movimiento',
    description: 'Deposito de salario',
    amount: '1000',
  },
  {
    id: 2,
    title: 'Movimiento 1',
    description: 'Deposito de honorarios',
    amount: '500',
  },
  {
    id: 3,
    title: 'Movimiento 3',
    description: 'Comida',
    amount: '-100',
  },
  {
    id: 4,
    title: 'Movimiento 4',
    description: 'Colegiatura',
    amount: '1000',
  },
  {
    id: 5,
    title: 'Movimiento 5',
    description: 'Reparación equipo',
    amount: '1000',
  },
]
</script>
<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume :label="'31 de diciembre'" :totalAmount="20000" :amount="10000">
        <template #graphic> graphic </template>
        <template #action> <Action /></template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" />
    </template>
  </Layout>
</template>
