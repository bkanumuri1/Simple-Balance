<script>
export default {
    name: 'Balance',
    props: {
      curr: String
    },
    data() {
        return {
            balance: 100,
            amount: 10,
        }
    },
    emits: ['newBal', 'newAmt'], 
    computed: {
        balanceString() {
            return `Account Balance: ${this.balance}`;
        }
    },
    watch: {
      amount: function(newAmt, oldAmt) {
         if (oldAmt !== newAmt) {
            this.$emit('newAmt', newAmt);
         }
      }
    },
    methods: {
        addBalance() {
            this.balance += this.amount
            this.$emit('newBal', this.balance);

        },
        subtractBalance() {
            if (this.amount <= this.balance) {
              this.balance -= this.amount
              this.$emit('newBal', this.balance);
            }
        }
    },
    mounted() {
        console.log('Application mounted');
        this.$emit('newAmt', this.amount);
        this.$emit('newBal', this.balance);
    },
}
</script>

<template>
    <div class="greetings">
      <h3>{{balanceString}} {{curr}}</h3>
      <h3>Amount: {{ amount }} {{curr}}</h3>
      <h3>Change amount to: <input type="range" min="5" max="100" step="5" v-model.number="amount" class="slider" id="myRange"></h3>
      <button @click="addBalance">Add</button> &nbsp;
      <button @click="subtractBalance">Subtract</button>
      <br>
    </div>
  </template>
  
  <style scoped>
  h1 {
    font-weight: 500;
    font-size: 2.6rem;
    top: -10px;
  }
  
  h3 {
    font-size: 1.2rem;
  }
  
  .greetings h1,
  .greetings h3 {
    text-align: center;
  }
  
  @media (min-width: 1024px) {
    .greetings h1,
    .greetings h3 {
      text-align: left;
    }
  }
  </style>