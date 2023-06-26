<template>
  <div>
    <!-- アプリのUIコンポーネント -->
    <h1>財務会計アプリ</h1>
    <p>残高: {{ balance }}</p>
    <input type="number" v-model="transactionAmount" placeholder="金額を入力してください">
    <button @click="addTransaction">入金</button>
    <button @click="withdrawTransaction">引き出し</button>

    <!-- 履歴 -->
    <h2>履歴</h2>
    <ul>
      <li v-for="transaction in transactionHistory" :key="transaction.id">
        {{ transaction.description }} - {{ transaction.amount }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      balance: 0,
      transactionAmount: 0,
      transactionHistory: []
    };
  },
  methods: {
    addTransaction() {
      // 入金処理
      const transaction = {
        id: Date.now(),
        description: "入金",
        amount: this.transactionAmount
      };
      this.transactionHistory.push(transaction);
      this.balance += this.transactionAmount;
      this.transactionAmount = 0;
    },
    withdrawTransaction() {
      // 引き出し処理
      if (this.transactionAmount > this.balance) {
        alert("残高が不足しています");
        return;
      }

      const transaction = {
        id: Date.now(),
        description: "引き出し",
        amount: -this.transactionAmount // 引き出しは負の値として表現する
      };
      this.transactionHistory.push(transaction);
      this.balance -= this.transactionAmount;
      this.transactionAmount = 0;
    }
  }
};
</script>
