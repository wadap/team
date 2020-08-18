<template>
  <div>
    <nav class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item" href="../"> </a>
          <span class="navbar-burger burger" data-target="navbarMenu">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenu" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">Home</a>
            <a class="navbar-item">Examples</a>
            <div class="navbar-item has-dropdown is-hoverable">
              <a class="navbar-link">Account</a>
              <div class="navbar-dropdown">
                <a class="navbar-item">Dashboard</a>
                <a class="navbar-item">Profile</a>
                <a class="navbar-item">Settings</a>
                <hr class="navbar-divider" />
                <div class="navbar-item">Logout</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <div class="container">
      <nuxt />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' },
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' },
        },
      ],
    }
  },
}
</script>
