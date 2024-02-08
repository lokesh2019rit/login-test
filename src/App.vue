<template>
  <div id="app">
    <div id="auth-container">
      <h2 id="form-title">{{ formTitle }}</h2>
      <b-form v-if="isRegistration" @submit.prevent="register">
        <label for="username">Username:</label>
        <input type="text" v-model="registerData.username" placeholder="Please enter the Username" required>
        <label for="phone">Phone Number:</label>
        <div id="phone-input-container">
          <select v-model="registerData.countryCode">
            <option value="+91">+91 (IND)</option>
            <option value="+1">+1  (USA)</option>
            <option value="+44">+44 (UK)</option>
            <!-- Add more country codes as needed -->
          </select>
          <input type="tel" v-model="registerData.phone" placeholder="Please enter the Phone number" required>
        </div>
        <label for="new-password">New Password:</label>
        <input type="password" v-model="registerData.newPassword" placeholder="Please enter the password"  required>
        <label for="confirm-password">Confirm Password:</label>
        <input type="password" v-model="registerData.confirmPassword" placeholder="Please re-enter the password" required>
        <button type="submit">Register</button>
      </b-form>

      <form v-else @submit.prevent="login">
        <div id="login-options">
          <button @click="setLoginOption('phone')">Login with Phone</button>
          <button @click="setLoginOption('email')">Login with Email</button>
        </div>
        <label v-if="loginOption === 'phone'" for="login-phone">Phone Number:</label>
        <label v-else for="login-email">Email:</label>
        <div id="phone-input-container" v-if="loginOption === 'phone'">
          <select v-model="loginData.countryCode">
            <option value="+91">+91 (IND)</option>
            <option value="+1">+1  (USA)</option>
            <option value="+44">+44 (UK)</option>
            <!-- Add more country codes as needed -->
          </select>
          <input type="tel" v-model="loginData.phone" v-if="loginOption === 'phone'" placeholder="Please enter the Phone number" required>
        </div>
        <input type="email" v-model="loginData.email" v-else placeholder="Please enter the email" required>
        <label for="login-password">Password:</label>
        <input type="password" v-model="loginData.password" placeholder="Please enter the Password" required>
        <button type="submit">Login</button>
        <div id="login-links">
          <p id="forgot-password-link" @click="forgotPassword">Forgot Password?</p>
          <p id="customer-service-link" @click="customerService">Customer Service</p>
        </div>
      </form>

      <p id="toggle-form-link" @click="toggleForm">{{ toggleLinkText }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isRegistration: true,
      formTitle: 'Registration Page',
      toggleLinkText: 'Already have an account? Login here',
      loginOption: 'phone', // Default login option
      registerData: {
        username: '',
        countryCode: '+1',
        phone: '',
        newPassword: '',
        confirmPassword: '',
      },
      loginData: { 
        email: '', // Added email field for email login
        countryCode: '+1',
        phone: '',
        password: '' 
      },
    };
  },
  methods: {
    register() {
      // Registration logic
      console.log('Registration logic');
    },
    login() {
      // Login logic
      console.log('Login logic');
    },
    toggleForm() {
      this.isRegistration = !this.isRegistration;
      this.formTitle = this.isRegistration ? 'Registration Page' : 'Login Page';
      this.toggleLinkText = this.isRegistration ? 'Already have an account? Login here' : 'Don\'t have an account? Register here';
    },
    forgotPassword() {
      // Forgot password logic
      console.log('Forgot password logic');
    },
    customerService() {
      // Customer service logic
      console.log('Customer service logic');
    },
    setLoginOption(option) {
      // Switch between phone and email login options
      this.loginOption = option;
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(to right, #e4e9ed, #2c3e50);
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

#auth-container {
  background-color: #ece9e9;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  padding: 40px;
  text-align: center;
}
h2 {
  color: #333;
  background:purple;
  color:white;
  margin-bottom:2px;
  padding:5px;
  border-radius: 30px;
}

h2{
  animation: blink 1s infinite alternate;
}

@keyframes blink {
  from { background-color: purple; }
  to { background-color: red; }
}

label {
  display: flex;
  margin: 15px 0;

}

input{
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 10px;

}
select{
  width: 70px;
  padding: 10px;
  box-sizing: border-box;
  margin-bottom: 15px;
  margin-right: 15px;
  border: 1px solid #ccc;
  border-radius: 10px;
}

#phone-input-container {
  display: flex;
  align-items: center;
  font-size: 14px;
}

button, #toggle-form-link, #forgot-password-link, #customer-service-link {
  background-color: #fc2e17;
  color: white;
  padding: 10px 25px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 10px;
  border-radius: 30px;
}

button:hover {
  background-color: #0056b3;
}

a {
  color: #007bff;
  text-decoration: none;
}

#login-options {
  display: flex;
  justify-content:space-around;
  gap: 10px;
  margin-bottom: 20px;
  margin-top: 15px;
}

#login-links {
  display:inline-flexbox;
  flex-direction: column;
  align-items: center;
}
</style>