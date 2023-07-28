html
Copy code
<template>
  <q-page class="login-page">
    <div class="login-container">
      <q-card class="login-card">
        <q-card-section>
          <div class="login-title">Sign In</div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="submitForm">
            <q-input dense filled v-model="formData.email" label="Email" class="input-field"></q-input>
            <q-input dense filled v-model="formData.password" type="password" label="Password" class="input-field"></q-input>
            <q-btn type="submit" color="primary" label="Sign In" :loading="isLoginLoading" @click="SuccessLogin"></q-btn>
          </q-form>
        </q-card-section>
        <q-card-section class="text-center">
          <div class="login-form-footer">
            <a href="#" class="forgot-password-link">Forgot Password?</a>
            <div class="signup-link">Don't have an account? <router-link to="/signup" class="signup-link-text">Sign Up</router-link></div>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<style lang="scss" scoped>
.login-page {
  position: relative;
  height: 100vh;
  display: flex;
  justify-content: center; /* Center horizontally */
  align-items: center; /* Center vertically */
  font-family: 'Helvetica Neue', Arial, sans-serif;   
}

.login-container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
}

.background-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('path_to_your_background_image.jpg');
  background-size: cover;
  background-position: center;
  filter: blur(4px);
  z-index: -1;
}

.login-card {
  max-width: 500px; /* Increased width */
  height: 450px; /* Increased height */
  border-radius: 8px;
  padding: 40px; /* Increased padding */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(8px);
  animation: fadeIn 1s;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.login-title {
  font-size: 32px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 30px;
  color: #333;
}

.q-card-section {
  margin: 15px 0;
}

.signup-link {
  font-size: 16px;
  color: #777;
}

.text-dark {
  color: #111;
}

.q-btn[type="submit"] {
  width: 100%;
}

.input-field {
  margin-bottom: 20px;
}

</style>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "SignUp",

  data() {
    return {
      formData: {
        email: "",
        password: "",
      },
      isLoginLoading: false,
    };
  },
  methods: {
    async submitForm() {
      try {
        this.isLoginLoading = true;
        // Simulate login delay
        await new Promise((resolve) => setTimeout(resolve, 1500));
        // Replace the next line with your actual API call
        // console.log("Simulated login success");
        // this.formData.email = "";
        // this.formData.password = "";
        const response = await this.$axios.post('http://192.168.1.44:4000/v1/login', this.formData );
        console.log("Response: ", response.data);
        this.$router.push('/success');
      } catch (error) {
        console.error("Error", error);
        alert("Failed to login. Please try again.");
      } finally {
        this.isLoginLoading = false;
      }
    },
  },
});
</script>



<!-- <template>
  <div class="container">
    <q-page class="flex flex-center">
      <q-card class="login-card">
        <q-card-section>
          <div class="login-title">
            Login Page
          </div>
        </q-card-section>
        <q-card-section>
          <q-form @submit="submit">
            <div class="input-label">Username</div>
            <q-input dense filled v-model="formData.email" unelevated />
            <div class="input-label">Password</div>
            <q-input dense filled v-model="formData.password" unelevated type="password" />
            <div class="submit">
              <q-btn  color="primary" type="submit" label="Sign In"/>
              <q-btn color="secondary" flat label="RESET" @click="reset" />
            </div>
          </q-form>
        </q-card-section>
      </q-card>
    </q-page>
  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
}

.login-card {
  max-width: 500px;
  border-radius: 5px;
  padding: 30px; 
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
}

.login-title {
  font-size: 28px; 
  font-weight: bold;
  text-align: center;
  margin-bottom: 20px;
}

.input-label {
  font-size: 16px; 
  margin-bottom: 5px;
}

.text__input {
  margin-bottom: 15px;
}

.submit {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 10px;
  justify-items: center;
  margin-top: 15px;
}
</style>


<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data() {
    return {
      formData: {
        email: '',
        password: ''
      },
      isLoginLoading: false
    }
  },
  methods:{
    async submit() {
      try {
        this.isLoginLoading = true;
        console.log('Form Data:', this.formData);
        // const response = await this.$axios.post('http://localhost:4000/v1/login', this.formData );
        console.log("Response: ", response.data);
        this.formData.email = '';
        this.formData.password = '';
      } catch (error) {
        console.error("Error", error);x
        alert(error.response.data.message);
      } finally {
        this.isLoginLoading = false;
      }
    },
    reset() {
      this.formData.email = '';
      this.formData.password = '';
    }
  }
})
</script> -->
