<template>
  <div id="app">
    <v-app id="inspire">
      <v-form >
        <v-container>
          <v-row>
            <v-col cols="12" md="4">
              <v-text-field
                v-model="firstname"
                label="First name"
                required
              ></v-text-field>
            </v-col>

            <v-col cols="12" md="4">
              <v-text-field
                v-model="lastname"
                label="Last name"
                required
              ></v-text-field>
            </v-col>
           
            <v-col cols="12" md="4">
              <v-text-field v-model="email"  label="E-mail" required></v-text-field>
            </v-col>
          </v-row>
        </v-container>
        <v-btn @click="testFunction">test</v-btn>
        <v-btn @click="insertFunction">Post</v-btn>
      </v-form>
    </v-app>
  </div>
</template>

<script>
// const axios = require("axios");
import axios from "axios"

export default {
    data: function(){
        return {
            firstname: "",
            lastname: "",
            email: ""
        }
    },
  methods: {
    testFunction() {
      axios
        .get("http://localhost:3333/alltest").then((res)=> {
            // eslint-disable-next-line no-console
            console.log(res) 
        }).catch((err)=> {
            // eslint-disable-next-line no-console
            console.log(err) 
        })

    },
    insertFunction(){
         // eslint-disable-next-line no-console
         let objectToSend = {
             firstname: this.firstname,
            lastname: this.lastname,
            email: this.email
         }
          // eslint-disable-next-line no-console
        console.log("buttton insert jalan");
        axios.post("http://localhost:3333/insertTest", objectToSend).then((res)=> {
            // eslint-disable-next-line no-console
            console.log(res)
        }).catch((err) => {
            // eslint-disable-next-line no-console
            console.log(err)
        })
    }
  }
};
</script>

<style scoped>
</style>