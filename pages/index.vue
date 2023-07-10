<template>
  <div>
    <!-- ナビゲーションバー -->
    <nav>
      <ul>
        <li><a href="#">財務会計アプリ</a></li>
      </ul>
    </nav>

    <!-- アプリのUIコンポーネント -->
    <p style="color:#0FF">残高 </p>
    <p>{{ balance }}</p>
    <input type="number" v-model="transactionAmount" placeholder="金額を入力してください" />
    <button @click="addTransaction">入金</button>
    <button @click="withdrawTransaction">引き出し</button>

    <!-- 履歴 -->
    <h2 style="color:#0FF">履歴</h2>
    <ul>
      <li v-for="transaction in transactionHistory" :key="transaction.id">
        {{ transaction.description }} - {{ transaction.amount }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const balance = ref(0);
const transactionAmount = ref(0);
const transactionHistory = ref([]);

const addTransaction = () => {
  // 入金処理
  const transaction = {
    id: Date.now(),
    description: '入金',
    amount: transactionAmount.value,
  };
  transactionHistory.value.push(transaction);
  balance.value += transactionAmount.value;
  transactionAmount.value = 0;
};

const withdrawTransaction = () => {
  // 引き出し処理
  if (transactionAmount.value > balance.value) {
    alert('残高が不足しています');
    return;
  }

  const transaction = {
    id: Date.now(),
    description: '引き出し',
    amount: -transactionAmount.value, // 引き出しは負の値として表現する
  };
  transactionHistory.value.push(transaction);
  balance.value -= transactionAmount.value;
  transactionAmount.value = 0;
};
</script>

<style>
nav {
  background-color: #333;
  color: #fff;
}

nav ul {
  list-style: none;
  display: flex;
  justify-content: space-around;
  padding: 0;
}

nav ul li {
  margin: 10px;
}

nav ul li a {
  color: #fff;
  text-decoration: none;
}
</style>
