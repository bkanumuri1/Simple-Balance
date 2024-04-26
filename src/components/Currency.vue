<script>
export default {
   props: {
      amt: Number
   },
   watch: {
      amt: function(newAmt, oldAmt) {
         if (oldAmt !== newAmt || this.amount !== newAmt) {
            this.amount = newAmt;
         }
      },
      convertfrom: function(newCnt, oldCnt) {
         if (oldCnt !== newCnt) {
            this.$emit('newCurr', newCnt);
         }
      }
   },
   data() {
      return {
         name:'DB',
         currencyfrom : [
            {name:"USD", desc:"US Dollar"},
            {name:"EUR", desc:"Euro"},
            {name:"INR", desc:"Indian Rupee"},
            {name:"BHD", desc:"Bahraini Dinar"}
         ],
         convertfrom: "INR",
         convertto:"USD",
         amount :"",
         curr:"USD"
      }
   },
   emits: ['newCurr'],
   computed :{
      finalamount:function() {
         var to = this.convertto;
         var from = this.convertfrom;
         var final;
         switch(from) {
            case "INR":
            if (to == "USD") {
               final = this.amount * 0.016;
            }
            if (to == "EUR") {
               final = this.amount * 0.013;
            }
            if (to == "INR") {
               final = this.amount;
            }
            if (to == "BHD") {
               final = this.amount * 0.0059;
            }
            break;
            case "USD":
            if (to == "INR") {
               final = this.amount * 63.88;
            }
            if (to == "EUR") {
               final = this.amount * 0.84;
            }
            if (to == "USD") {
               final = this.amount;
            }
            if (to == "BHD") {
               final = this.amount * 0.38;
            }
            break;
            case "EUR":
            if (to == "INR") {
               final = this.amount * 76.22;
            }
            if (to == "USD") {
               final = this.amount * 1.19;
            }
            if (to == "EUR") {
               final = this.amount;
            }
            if (to == "BHD") {
               final = this.amount * 0.45;
            }
            break;
            case "BHD":
            if (to == "INR") {
               final = this.amount *169.44;
            }
            if (to == "USD") {
               final = this.amount * 2.65;
            }
            if (to == "EUR") {
               final = this.amount * 2.22;
            }
            if (to == "BHD") {
               final = this.amount;
            }
            break
         }
         return final;
      }
   },
}
</script>

<template>
      <div id="databinding" >
         <h1>Currency Converter</h1>
         <span>Enter Amount:</span>
         <input class="amountInput" type="number" v-model.number="amount" placeholder="10"/><br>
         <span>Convert From:&nbsp;</span> 
         <select v-model="convertfrom" style="convertSelect">
            <option v-for="(a, index) in currencyfrom"  v-bind:value="a.name">{{a.desc}}</option>
         </select><br>
         <span>Convert To: &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
         <select v-model="convertto" style="convertSelect">
            <option v-for="(a, index) in currencyfrom" v-bind:value="a.name">{{a.desc}}</option>
         </select><br>
         <span> {{amount}} {{convertfrom}} equals {{finalamount}} {{convertto}}</span>
      </div>
</template>

<style>
      #databinding{
            padding: 10px 20px 20px 20px;
            margin: 0 0 25px 0;
            width: auto;
            background-color: #e7e7e7;
      }
      span, option, input {
            font-size:15px;
            margin: 15px;
      }
      .amountInput{
        margin: 10px;
      }
      .convertSelect{
        width:300px;
        font-size:15px;
      }
    
</style>