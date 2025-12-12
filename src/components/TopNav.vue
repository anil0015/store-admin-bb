<template>
  <nav>
    <div class="brand-container">
      <a href="/" class="bby-logo">
        <span class="tag">
          BEST BUY
        </span>
      </a>
      <span class="portal-name">Admin Portal</span>
    </div>

    <ul class="nav-links" :class="{ 'nav-links--open': isNavOpen }">
      <li><router-link to="/orders" @click="closeNav">Orders</router-link></li>
      <li><router-link to="/products" @click="closeNav">Products</router-link></li>
      <li><a href="#" @click="closeNav">Account</a></li>
    </ul>

    <button class="hamburger" @click="toggleNav">
      <span class="hamburger-icon"></span>
    </button>
  </nav>
</template>

<script>
export default {
  name: 'TopNav',
  data() {
    return {
      isNavOpen: false
    }
  },
  methods: {
    toggleNav() {
      this.isNavOpen = !this.isNavOpen
    },
    closeNav() {
      this.isNavOpen = false
    }
  }
}
</script>

<style scoped>
/* --- Best Buy Color Vars --- */
:root {
  --bby-blue: #0046BE;
  --bby-yellow: #FFF200;
  --bby-black: #000000;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #0046BE; /* Official Blue */
  color: #fff;
  padding: 1rem 2rem;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  font-family: 'Human BBY', Arial, Helvetica, sans-serif; /* Mimic their font */
  border-bottom: 4px solid #003b9f;
}

/* --- Brand Section --- */
.brand-container {
  display: flex;
  align-items: center;
  gap: 15px;
}

/* The CSS Tag Logo */
.bby-logo {
  text-decoration: none;
  display: inline-block;
}

.bby-logo .tag {
  background-color: #FFF200; /* Official Tag Yellow */
  color: #000;
  font-weight: 900;
  font-size: 1.2rem;
  padding: 8px 12px;
  line-height: 1;
  display: flex;
  align-items: flex-end;
  /* subtle tag shape styling */
  position: relative;
}

.portal-name {
  font-size: 1.2rem;
  font-weight: 400;
  color: #fff;
  border-left: 1px solid rgba(255,255,255,0.3);
  padding-left: 15px;
}

/* --- Links --- */
.nav-links {
  display: flex;
  list-style: none;
  gap: 25px;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: #fff;
  text-decoration: none;
  font-weight: 700;
  font-size: 1rem;
  text-transform: capitalize;
}

.nav-links a:hover {
  color: #FFF200;
  text-decoration: underline;
  text-underline-offset: 5px;
}

/* --- Mobile Hamburger --- */
.hamburger {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
}

.hamburger-icon {
  display: block;
  width: 25px;
  height: 3px;
  background-color: #fff;
  position: relative;
}

.hamburger-icon::before,
.hamburger-icon::after {
  content: '';
  display: block;
  width: 25px;
  height: 3px;
  background-color: #fff;
  position: absolute;
  left: 0;
}
.hamburger-icon::before { top: -8px; }
.hamburger-icon::after { bottom: -8px; }

/* --- Responsive --- */
@media (max-width: 768px) {
  .nav-links {
    display: none;
    flex-direction: column;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background-color: #0046BE;
    padding: 1rem;
    border-top: 1px solid #003b9f;
  }

  .nav-links--open {
    display: flex;
  }

  .nav-links li {
    padding: 10px 0;
    border-bottom: 1px solid rgba(255,255,255,0.1);
  }

  .hamburger {
    display: block;
  }
}
</style>