<template>
  <div class="review">
    <h3>Review Registrant Information</h3>
      <ul>
        <li><b>Name:</b> {{curRegistrant.name}}</li>  
        <li><b>Email:</b> {{curRegistrant.email}}</li>  
        <li><b>Address:</b> {{curRegistrant.addr1}}; {{curRegistrant.addr2}}</li>
        <li><b>Affiliation:</b> {{curRegistrant.affiliation}} &nbsp; , &nbsp; 
            {{curRegistrant.status}}</li> 
        <li><b>Date:</b> {{curRegistrant.date}}</li>
        <li><b>Payment Method:</b> {{curRegistrant.payment}}</li>  
        <li v-show="btnvis"><button class="btnBack" @click="goback">Back</button></li>
        <li v-show="btnvis"><button class="btnReg" @click="finish">Register</button></li>
        <li v-show="!btnvis"><h3 style="color:green">Registration Successful!</h3></li>
      </ul>      
  </div>
</template>

<script>
export default {
  name: 'Review',
  props: ["curRegistrant"],
  data() {
    return {
      btnvis: true
    }
  },
  methods: {
    finish() {
      this.btnvis = !this.btnvis;
    },
    goback() {
      this.$emit("go-back");
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

.btnReg {
  border: none;
  background: #42b983;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btnReg:hover {
  background: #174625;
}

.btnBack {
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btnBack:hover {
  background: rgb(201, 93, 89);
}

ul#statusmenu li {
  display:inline;
}
ul#paymenu li {
  display: inline;
}
</style>
