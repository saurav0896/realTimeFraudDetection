<template>
  <v-app>
    <template v-if="home == false">
      <v-container id="login" fluid style="height: 90vh; padding: 1px">
        <v-vanta effect="net" :options="options"></v-vanta>
        <v-card class="form-container elevation-4">
          <div class="pa-8">
            <h3 style="color: #008dd3">Please Login to Continue</h3>
            <form>
              <v-text-field
                v-model="name"
                :error-messages="nameErrors"
                :counter="10"
                label="Name"
                required
                @input="$v.name.$touch()"
                @blur="$v.name.$touch()"
              ></v-text-field>
              <v-text-field
                v-model="email"
                :error-messages="emailErrors"
                label="E-mail"
                required
                @input="$v.email.$touch()"
                @blur="$v.email.$touch()"
              ></v-text-field>
              <v-text-field
                label="Mobile Number"
                v-model="callerNumber"
                required
              ></v-text-field>
              <v-btn class="mr-4" @click="submit" color="primary">
                submit
              </v-btn>
              <v-btn @click="clear" color="error"> clear </v-btn>
            </form>
          </div>
          <div class="pa-4">
            <v-alert v-if="failure" type="error" dense
              >Please connect with support team
              <strong>support@example.com</strong> for more help</v-alert
            >
            <v-alert v-if="success" type="success" dense
              >User Validation is successful</v-alert
            >
          </div>
        </v-card>
      </v-container>
    </template>
    <template v-else>
      <v-container
        id="home"
        fluid
        style="background-color: #008dd3; height: 75vh"
      >
        <v-row>
          <v-col cols="6" class="text-center white--text">
            <div style="padding-top: 6rem">
              <h2 style="font-size: 50px">Mega Shop</h2>
              <h4 style="font-size: 20px">Shop at your finger tip...</h4>
              <p class="pa-10">
                Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quas
                suscipit modi dignissimos quam recusandae laboriosam aperiam
                earum repellat illum officiis!
              </p>
              <v-btn outlined color="white">Get Started</v-btn>
            </div>
          </v-col>
          <v-col cols="6">
            <img src="../assets/Banner.png" alt="" />
          </v-col>
        </v-row>
      </v-container>
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320">
        <path
          fill="#008DD3"
          fill-opacity="1"
          d="M0,0L48,16C96,32,192,64,288,112C384,160,480,224,576,208C672,192,768,96,864,64C960,32,1056,64,1152,69.3C1248,75,1344,53,1392,42.7L1440,32L1440,0L1392,0C1344,0,1248,0,1152,0C1056,0,960,0,864,0C768,0,672,0,576,0C480,0,384,0,288,0C192,0,96,0,48,0L0,0Z"
        ></path>
      </svg>
      <v-container>
        <h1 class="text-center"> Latest Collections</h1>
        <v-row>
          <v-col cols="4">
            <v-card class="mx-auto my-12" max-width="374">
              <v-img
                height="350"
                src="https://indiater.com/wp-content/uploads/2019/05/1.jpg"
              ></v-img>

              <v-card-title>Mens Collections</v-card-title>
              <v-card-text>
                <v-row align="center" class="mx-0">
                  <v-rating
                    :value="4.5"
                    color="amber"
                    dense
                    half-increments
                    readonly
                    size="14"
                  ></v-rating>

                  <div class="grey--text ms-4">4.5 (2386)</div>
                </v-row>
                <v-chip-group
                  v-model="selection"
                  active-class="deep-purple accent-4 white--text"
                  column
                >
                  <v-chip>Add to Cart</v-chip>

                  <v-chip>Buy Now</v-chip>
                </v-chip-group>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="4">
            <v-card class="mx-auto my-12" max-width="374">
              <v-img
                height="350"
                src="https://indiater.com/wp-content/uploads/2019/05/free-women-wear-leggings-sale-banner-design-template.jpg"
              ></v-img>

              <v-card-title>WoMens Collections</v-card-title>

              <v-card-text>
                <v-row align="center" class="mx-0">
                  <v-rating
                    :value="4.5"
                    color="amber"
                    dense
                    half-increments
                    readonly
                    size="14"
                  ></v-rating>

                  <div class="grey--text ms-4">4.1 (4183)</div>
                </v-row>
                <v-chip-group
                  v-model="selection"
                  active-class="deep-purple accent-4 white--text"
                  column
                >
                  <v-chip>Add to Cart</v-chip>

                  <v-chip>Buy Now</v-chip>
                </v-chip-group>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="4">
            <v-card class="mx-auto my-12" max-width="374">
              <v-img
                height="350"
                src="https://indiater.com/wp-content/uploads/2019/03/kids-wear-fashion-social-media-banner-psd.jpg"
              ></v-img>

              <v-card-title>Kids Collections</v-card-title>
              <v-card-text>
                <v-row align="center" class="mx-0">
                  <v-rating
                    :value="4.5"
                    color="amber"
                    dense
                    half-increments
                    readonly
                    size="14"
                  ></v-rating>

                  <div class="grey--text ms-4">4.8 (1413)</div>
                </v-row>
                <v-chip-group
                  v-model="selection"
                  active-class="deep-purple accent-4 white--text"
                  column
                >
                  <v-chip>Add to Cart</v-chip>

                  <v-chip>Buy Now</v-chip>
                </v-chip-group>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </template>
  </v-app>
</template>

<script>
import { validationMixin } from "vuelidate";
import { required, maxLength, email } from "vuelidate/lib/validators";
import axios from "axios";
import VVanta from "vue-vanta";

export default {
  name: "Login",
  mixins: [validationMixin],
  components: { VVanta },
  validations: {
    name: { required, maxLength: maxLength(10) },
    email: { required, email },
    select: { required },
    checkbox: {
      checked(val) {
        return val;
      },
    },
  },
  data() {
    return {
      options: {
        mouseControls: true,
        touchControls: true,
        minHeight: 600.0,
        minWidth: 200.0,
        scale: 1.0,
        scaleMobile: 1.0,
        color: 0xffffff,
        backgroundColor: 0x71d2,
      },
      name: "",
      email: "",
      select: null,
      callerNumber: null,
      failure: null,
      success: null,
      home: false,
    };
  },
  computed: {
    checkboxErrors() {
      const errors = [];
      if (!this.$v.checkbox.$dirty) return errors;
      !this.$v.checkbox.checked && errors.push("You must agree to continue!");
      return errors;
    },
    selectErrors() {
      const errors = [];
      if (!this.$v.select.$dirty) return errors;
      !this.$v.select.required && errors.push("Item is required");
      return errors;
    },
    nameErrors() {
      const errors = [];
      if (!this.$v.name.$dirty) return errors;
      !this.$v.name.maxLength &&
        errors.push("Name must be at most 10 characters long");
      !this.$v.name.required && errors.push("Name is required.");
      return errors;
    },
    emailErrors() {
      const errors = [];
      if (!this.$v.email.$dirty) return errors;
      !this.$v.email.email && errors.push("Must be valid e-mail");
      !this.$v.email.required && errors.push("E-mail is required");
      return errors;
    },
  },

  methods: {
    submit() {
      const apiClient = axios.create({
        withCredentials: false,
        baseURL:
          "https://dev94962.service-now.com/api/now/table/u_fraud_call_list?sysparm_limit=1&u_caller_number_1=" +
          this.callerNumber,
        headers: {
          Accept: "application/json",
          "Access-Control-Allow-Origin": "*",
          "Content-Type": "application/json",
          Authorization: "Basic YWRtaW46WmVuc2FyQDEyMw==",
        },
      });
      var self = this;
      apiClient.get().then(function (response) {
        console.log("response value", response);
        if (response.data.result.length === 0) {
          self.home = true;
          self.failure = false;
          self.success = true;
        } else {
          console.log("Success");
          self.success = false;
          self.failure = true;
        }
      });
    },

    clear() {
      this.$v.$reset();
      this.name = "";
      this.email = "";
      this.select = null;
      this.checkbox = false;
      this.callerNumber = "";
      this.success = false;
      this.failure = false;
    },
  },
};
</script>
<style scoped>
.form-container {
  width: 40%;
  margin: 80px auto;
  text-align: center;
}
</style>
