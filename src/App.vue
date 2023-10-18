<template>
  <div class="app">
    <HeaderComponent :loggedIn="loggedIn" @user-logged-in="onUserLoggedIn" @user-logged-out="onUserLoggedOut" />
    
    <div class="app-content">
      <div class="components-section">
        <NavigationComponent v-if="loggedIn" :activePage="activeComponent" @navigate="onNavigationChange" />
        <HomeComponent v-if="loggedIn && activeComponent === 'home'" />
        <AboutMeComponent v-if="loggedIn && activeComponent === 'aboutMe'" />
      </div>
    </div>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavigationComponent from './components/NavigationComponent.vue';
import HomeComponent from './components/HomeComponent.vue';
import AboutMeComponent from './components/AboutMeComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    NavigationComponent,
    HomeComponent,
    AboutMeComponent
  },
  data() {
    return {
      loggedIn: false,
      activeComponent: 'home'
    };
  },
  methods: {
    onUserLoggedIn() {
      this.loggedIn = true;
      this.activeComponent = 'home';
    },
    onUserLoggedOut() {
      const userConfirmation = confirm('Would you like to log out?');
      if (userConfirmation) {
        this.loggedIn = false;
      }
    },
    onNavigationChange(component) {
      this.activeComponent = component;
    }
  }
};
</script>

<style>
.app {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(8, 2, 15);
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.app-content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
}

.components-section {
  margin-top: 100px;
  margin-left: 50px;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
</style>
