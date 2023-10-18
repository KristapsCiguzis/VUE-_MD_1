<template>
  <div class="header">
    <div class="logo-section">
      <img src="@/assets/logo.svg" alt="Logo" class="logo" />
      <span class="page-title">KRAKEN.FM</span>
    </div>
    <div class="menu-section">
      <div class="user-section">
        <div v-if="loggedIn" class="user-avatar">
          <div class="avatar-placeholder"></div>
        </div>
        <span v-if="loggedIn" class="user-name">Kristaps Ciguzis</span>
      </div>
      
      <div v-if="loggedIn" class="divider"></div> 
      
      <button @click="handleLoginLogout" class="login-logout-button">{{ loggedIn ? 'LOGOUT' : 'LOGIN' }}</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['loggedIn'],
  methods: {
    handleLoginLogout() {
      if (this.loggedIn) {
        this.$emit('user-logged-out');
      } else {
        const userConfirmation = confirm('Would you like to log in?');
        if (userConfirmation) {
          this.$emit('user-logged-in');
        }
      }
    }
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #1b1f38;
  padding: 20px 40px;
  width: 100%;
  color: white;
  font-family: 'Arial', sans-serif;
  position: fixed; 
  top: 0;
  left: 0;
  z-index: 1000; 
}

.logo-section {
  display: flex;
  align-items: center;
}

.logo {
  width: 50px;
  margin-right: 20px;
}

.page-title {
  font-size: 24px;
  font-weight: bold;
}

.menu-section {
  display: flex;
  align-items: center;
}

.user-name {
  margin-right: 20px;
  font-size: 18px;
}

.login-logout-button {
  padding: 10px 20px;
  background-color: transparent;
  border: none;
  font-size: 1rem;
  color: white;
  background-color: rgba(128, 0, 128, 0.5);
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.login-logout-button:hover {
  background-color: rgba(128, 0, 128, 0.5);
}

.user-section {
  display: flex;
  align-items: center;
}

.user-avatar {
  width: 40px; 
  height: 40px; 
  border-radius: 50%;
  background-color: #ccc; 
  margin-right: 10px; 
}

.divider {
  width: 1px;
  height: 30px; 
  background-color: white;
  margin: 0 10px; 
}





</style>

<style>
body, html {
  margin: 0;
  padding: 0;
}
</style>
