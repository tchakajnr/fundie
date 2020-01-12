<template>
  <v-dialog max-width="600px">
    <template v-slot:activator="{ on }">
      <v-btn class="success" dark v-on="on">
        <v-icon left dark>payment</v-icon>Pay
      </v-btn>
    </template>
    <v-card>
      <v-card-title>
        <h5>Pay in advance or Balance</h5>
      </v-card-title>
      <v-card-text>
        <v-form class="px-3" ref="form">
          <v-text-field
            v-model="title"
            label="Student Number"
            prepend-icon="person"
            :rules="inputRules"
          ></v-text-field>

          <v-text-field v-model="title" label="Note" prepend-icon="edit"></v-text-field>

          <v-menu lazy v-model="menu" :close-on-content-click="false">
            <v-text-field
              slot="activator"
              :value="formattedDate"
              clearable
              label="Due date"
              prepend-icon="date_range"
              :rules="inputRules"
            ></v-text-field>
            <v-date-picker
              v-model="date"
              :landscape="landscape"
              :show-current="showCurrent"
              :events="enableEvents ? functionEvents : null"
            ></v-date-picker>
          </v-menu>

          <v-spacer></v-spacer>
          <v-btn flat @click="submit" class="primary mr-3 mx-0 mt-3">
            <v-icon left>fab fa-alipay</v-icon>Pay with Alipay
          </v-btn>
          <v-btn flat @click="submit" class="success ml-0 mx-0 mt-3">
            <v-icon left>mdi-wechat</v-icon>Pay with Wechat
          </v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import format from "date-fns/format";
import db from "@/fb";

export default {
  data() {
    return {
      title: "",
      content: "",
      due: null,
      date: new Date(),
      menu: false,
      inputRules: [
        v => !!v || "This field is required",
        v => v.length >= 3 || "Minimum length is 3 characters"
      ]
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        const project = {
          title: this.title,
          content: this.content,
          due: format(this.due, "Do MMM YYYY"),
          person: "The Net Ninja",
          status: "ongoing"
        };
        db.collection("projects")
          .add(project)
          .then(() => {
            // console.log("added to db");
          });
      }
    }
  },
  computed: {
    formattedDate() {
      return this.due ? format(this.due, "Do MMM YYYY") : "";
    }
  }
};
</script>