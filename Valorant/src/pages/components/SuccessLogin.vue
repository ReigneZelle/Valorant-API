<template>
   <div id="master-wrap">
    <div id="logo-box">
      <div class="animated fast fadeInUp">
        <div class="icon"></div>
        <h1>Congratulations!</h1>
      </div>

      <div class="notice animated fadeInUp">
        <p class="lead">You have successfully logged in!</p>
        <div class="button-group">
          <router-link to="/home" class="btn animation go-to-home">Go to Home</router-link>
        </div>
      </div>
    </div>
  <!-- /#logo-box -->
</div>
<!-- /#master-wrap -->

</template>


  <style>
/*! Reset: normalize.css v3.0.2 | MIT License | git.io/normalize */

html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%
}

/* ... (other styles) ... */

/* Basic */
html {
  font-size: 16px;
  font-size: 1rem;
  line-height: 28px;
  line-height: 1.75rem;
}

body {
  background: #fff;
  margin: auto;
  color: #333;
}

/* Font family */
/* ... (other font styles) ... */

/* Button */
/* ... (button styles) ... */

/* Animation */
/* ... (animation styles) ... */

/* Layout: center box */
#logo-box {
  text-align: center;
  padding: 30px;
}

h1 {
  font-size: 30px;
  margin: 0 auto;
}

/* Desktop only */
@media (min-width: 481px) {
  #logo-box {
    position: absolute;
    text-align: center;
    left: 50%;
    top: 48%;
    width: 400px;
    margin-left: -230px;
    height: 440px;
    margin-top: -250px;
    font-size: 20px;
    border: 3px solid #999;
    box-shadow: 6px 6px 0px #333;
  }
  h1 {
    font-size: 36px;
  }
}

.icon {
  background: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCA4NDEuOSAxMTkwLjYiPjxwYXRoIGQ9Ik01NzMuMiAzNzMuNmwtMTguOS0xOC45TDM5Ni41IDUxNGwtODItODJMMjk3LjIgNDUxbDk5LjQgOTkuM0w1NzMuMiAzNzMuNnpNNzA1LjcgNDU1LjdWMTgyLjdIMTM3Ljh2MjcyLjlMOC40IDUwOS4zdjQ5OC41aDgyNS4xVjUwOS4zTDcwNS43IDQ1NS43ek03OTQuMSA1MjAuM2wtODguMyA1NS4ydi05MS41TDc5NC4xIDUyMC4zek02ODAuNCAyMDkuNnYzODMuM0w0MjEuNyA3NTMuOCAxNjMgNTkyLjlWMjA5LjZINjgwLjR6TTEzNy44IDU3NS42bC04OC40LTU1LjIgODguMy0zNi4zTDEzNy44IDU3NS42IDEzNy44IDU3NS42ek0zNS4zIDk4Mi41VjU0MC45bDM4Ni41IDI0NC41IDM4Ni40LTI0M3Y0NDEuN0gzNS4zVjk4Mi41ek0xMy40IDk5OC42bDQwOC40LTIxMi4yTTQyMi42IDc4Ni41TDgzMSA5OTguNyIgc3R5bGU9InN0cm9rZS13aWR0aDoyMDtzdHJva2U6IzAwMCIvPjwvc3ZnPg==) no-repeat center center;
  height: 128px;
  margin: auto;
  width: 90px;
}

#master-wrap {
  background-image: url('~src/assets/valorant.png'); /* Replace with the actual path to your image */
  background-size: cover; /* Adjust as needed */
  background-repeat: no-repeat; /* Adjust as needed */
  background-position: center center; /* Adjust as needed */
}

.notice {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.button-group {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 20px;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  cursor: pointer;
}

.go-to-home {
  background-color: #1C1D21;
}

.go-to-home:hover {
  background-color: #2d2e32;
}

.logout-btn {
  background-color: #e56b6f;
}

.logout-btn:hover {
  background-color: #ff8fa3;
}

  </style>
  
  <script>
import { defineComponent } from 'vue';
import HomePage from './HomePage.vue';

export default defineComponent({
  name: 'SuccessLogin',
  components: {
    HomePage
  },
  mounted() {
    // Redirection Counter
    var count = 20; // Timer
    var redirect = "/"; // Target URL

    function countDown() {
      var timer = document.getElementById("timer"); // Timer ID
      if (count > 0) {
        count--;
        timer.innerHTML = "This page will redirect in " + count + " seconds."; // Timer Message
        setTimeout(countDown, 1000);
      } else {
        this.$router.push('/home');
      }
    }

    countDown();
  },
});
</script>
  