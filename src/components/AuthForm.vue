<script setup>

</script>

<template>
  <div class="auth-container">
    <div class="title">
        Login or Register
    </div>

    <form action="" method="post" class="auth-form">
      <div class="field">
        <input type="text" name="username" id="username" :username="username">
        <label>Username</label>
      </div>

      <div id="username-error"></div>

      <div class="field">
        <input type="password" name="password" id="password" :password="password">
        <label>Password</label>
      </div>

      <div class="field">
        <input type="submit" value="Let's Play">
      </div>

      <div class="guest-link">
        Can't think of a good username? <a href="">Play as a Guest</a>
      </div>
    </form>
  </div>
</template>

<style scoped>
.auth-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #f9f9f9;
  padding: 20px;
}

.title {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 20px;
  color: #333;
}

.auth-form {
  width: 100%;
  max-width: 400px;
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.field {
  position: relative;
  margin-bottom: 20px;
}

.field input[type="text"],
.field input[type="password"],
.field input[type="submit"] {
  width: 90%;
  padding: 10px 15px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  outline: none;
}

.field label {
  position: absolute;
  top: 50%;
  left: 15px;
  font-size: 0.9rem;
  color: #aaa;
  pointer-events: none;
}

.field input[type="submit"] {
  background-color: #87c1ff;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
  border: none;
  transition: background-color 0.3s;
}

.guest-link {
  text-align: center;
  margin-top: 10px;
  font-size: 0.9rem;
}

.guest-link a {
  color: #007bff;
  text-decoration: none;
  transition: color 0.3s;
}
</style>
