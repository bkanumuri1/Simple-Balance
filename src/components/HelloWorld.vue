<script>
  export default {
    props: {
      name: String
    },
    data() {
        return {
            message: "Hello ",
            amt: 25
        }
    },
  }
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ message }} {{name}}</h1>
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

@media (min-width: 2048px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
