<template>
  <div class="regfields">
    <h3>Registrant Information</h3>
      <form @submit="registerNext">
        <ul>
          <li><input type="text"  id="name"  v-model="name"        name="name"        placeholder="Name..."></li>
          <li><input type="email" id="email" v-model="email"       name="email"       placeholder="Email..."></li>
          <li><input type="text"  id="addr1" v-model="addr1"       name="addr1"       placeholder="Street Address..."></li>
          <li><input type="text"  id="addr2" v-model="addr2"       name="addr2"       placeholder="City, State, Zip..."></li>
          <li><input type="text"  id="affil" v-model="affiliation" name="affiliation" placeholder="School/Company..."></li>
          <li><input type="date"  id="date"  v-model="date"        name="date"></li>
          <li>I am a...</li>
          <ul id="statusmenu">
            <li><input type="radio" name="status" id="ugrad" v-model="status" value="Undergrad Student"><label for="ugrad">Undergrad Student</label></li>
            <li><input type="radio" name="status" id="grad"  v-model="status" value="Grad Student"><label for="grad">Grad Student</label></li>
            <li><input type="radio" name="status" id="prof"  v-model="status" value="Professor"><label for="prof">Professor</label></li>
            <li><input type="radio" name="status" id="ind"   v-model="status" value="Industry Employee"><label for="ind">Industry Employee</label></li>
          </ul>
          <li>I will pay via...</li>
          <ul id="paymenu">
            <li><input type="radio" name="payment" id="credit" v-model="payment" value="Credit/Debit"><label for="credit">Credit/Debit</label></li>
            <li><input type="radio" name="payment" id="paypal" v-model="payment" value="PayPal"><label for="paypal">PayPal</label></li>
          </ul>
          <li><input type="submit" value="Next" class="btn"></li>
        </ul>
      </form>
  </div>
</template>

<script>
export default {
  name: 'RegisterFields',
  data() {
    return {
      name: '',
      email: '',
      addr1: '',
      addr2: '',
      affiliation: '',
      date: '2021-05-14',
      status: 'Undergrad Student',
      payment: 'Credit/Debit',
      good: true
    }
  },
  methods: {
    hl(id, highlight) {
      if(highlight)
        document.getElementById(id).style.background = "yellow";
      else
        document.getElementById(id).style.background = "white";
    },
    registerNext(e) {
    e.preventDefault();

      // reset
      this.good = true;
      this.hl("name",  false)
      this.hl("affil", false)
      this.hl("addr1", false)
      this.hl("addr2", false)
      this.hl("email", false)
      this.hl("addr1", false)
      this.hl("addr2", false)
      this.hl("addr2", false)
      // checks
      if (this.name.length < 3)        { this.good = false; this.hl("name",  true) }
      if (this.affiliation.length < 3) { this.good = false; this.hl("affil", true) }
      if (this.addr1.length < 3)       { this.good = false; this.hl("addr1", true) }
      if (this.addr2.length < 3)       { this.good = false; this.hl("addr2", true) }
      if (!this.email.includes('@'))   { this.good = false; this.hl("email", true) }
      if (!this.addr1.includes(' '))   { this.good = false; this.hl("addr1", true) }
      if (!this.addr2.includes(','))   { this.good = false; this.hl("addr2", true) }
      if (!this.addr2.includes(' '))   { this.good = false; this.hl("addr2", true) }

      if (this.good) {
        const registrant = {
          name: this.name,
          email: this.email,
          addr1: this.addr1,
          addr2: this.addr2,
          affiliation: this.affiliation,
          date: this.date,
          status: this.status,
          payment: this.payment
        }
        // Send to parent
        this.$emit("register-next", registrant);
      } else {
        alert("There are one or more issues with your submission.\nPlease make sure all data is valid and try again.")
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 7px 10px;
}
a {
  color: #42b983;
}

.btn {
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}

ul#statusmenu li {
  display:inline;
}
ul#paymenu li {
  display: inline;
}
</style>
