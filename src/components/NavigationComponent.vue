<template>
  <div class="navigation-container">
    <button :class="['navigation-button', { active: isActive('home') }]" @click="$emit('navigate', 'home')">HOME</button>
    <button :class="['navigation-button', { active: isActive('aboutMe') }]" @click="$emit('navigate', 'aboutMe')">ABOUT ME</button>
  </div>
</template>

<script>
export default {
  props: {
    activePage: {
      type: String,
      default: ''
    }
  },
  methods: {
    isActive(page) {
      return this.activePage === page;
    }
  }
};
</script>

<style>
.navigation-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.navigation-button {
  padding: 10px 20px;
  background-color: transparent;
  border: none;
  font-size: 1rem;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
.navigation-button.active {
  background-color: purple;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.2);
}

.navigation-button:hover {
  background-color: rgba(128, 0, 128, 0.5);
}
</style>
