<script>
import Balance from './components/Balance.vue'
import HelloWorld from './components/HelloWorld.vue'
import Currency from './components/Currency.vue';

export default {
  data() {
    return {
      fname: "Bhavana",
      bal: 0,
      curr: "",
      amt: 10,
    }
  },
  components: {
    Balance,
    HelloWorld,
    Currency
}
}
</script>

<template>
  <header>
    <div class="wrapper">
      <!-- <input v-model="fname"> -->
      <HelloWorld :name="this.fname" />
      <p>Account Balance: {{bal}} {{curr}} , Amount: {{amt}} {{curr}} </p>
      <Balance @new-bal="(v) => this.bal=v" @new-amt="(v) => this.amt=v" :curr="this.curr"/>
      <Currency @new-curr="(v) => this.curr=v" :amt="this.amt"/>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 4);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
