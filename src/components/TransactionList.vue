<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <li
      v-for="transaction in transactions"
      v-bind:key="transaction.id"
      v-bind:class="transaction.amount < 0 ? 'minus ' : 'plus'"
    >
      <!-- or :key="transaction.id"> -->
      <!-- :class="transaction.amount < 0 ? 'minus ' : 'plus'" -->

      {{ transaction.text }}
      <span>${{ transaction.amount }}</span>
      <button @click="deleteTransaction(transaction.id)" class="delete-btn">X</button>
    </li>
    <!-- <li class="minus">
      cash
      <span>-$400</span>
      <button class="delete-btn">X</button>
    </li>

    <li class="plus">
      Paycheck
      <span>$800</span>
      <button class="delete-btn">X</button>
    </li> -->
  </ul>
</template>

<script setup>
// export default {
//options Api

//   data() {
//     return {
//       transactions: [
//   { id: 1, text: 'Flower', amount: -19.99 },
//   { id: 2, text: 'salary', amount: 299.97 },
//   { id: 3, text: 'Book', amount: -10 },
//   { id: 4, text: 'camera', amount: 150 }
//       ]
//     }
//   }
//}

// export default {
//   //compositions Api - initial syntax

//   setup() {
//     const transactions = [
//       { id: 1, text: 'Flower', amount: -19.99 },
//       { id: 2, text: 'salary', amount: 299.97 },
//       { id: 3, text: 'Book', amount: -10 },
//       { id: 4, text: 'camera', amount: 150 }
//     ]

//     return {
//       transactions
//     }
//   }
// }

//new syntax

// const transactions = [
//   { id: 1, text: 'Flower', amount: -19.99 },
//   { id: 2, text: 'salary', amount: 299.97 },
//   { id: 3, text: 'Book', amount: -10 },
//   { id: 4, text: 'camera', amount: 150 }
// ]

import { defineProps } from 'vue'

const emit = defineEmits(['transactionDeleted'])

const props = defineProps({
  transactions: {
    type: Array,
    required: true
  }
})

const deleteTransaction = (id) => {
  emit("transactionDeleted", id)
}
</script>
                
<!-- transferring abo ve script t transaction to app.vue s that it will avalable globallys -->
