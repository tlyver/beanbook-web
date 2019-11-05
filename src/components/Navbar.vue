<template>
  <nav class="navbar is-fixed-top" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item">
        <img alt="Vue logo" src="../assets/bean.png">
      </a>

      <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div class="navbar-menu">
      <div class="navbar-start">
        <a class="navbar-item">
          About
        </a>

        <a class="navbar-item">
          Our Picks
        </a>

        <a class="navbar-item">
          Contact
        </a>
      </div>
      <div class="navbar-end">
        <div class="navbar-item">
          <div class="field has-addons">
            <div class="control">
              <input class="input is-small" type="text" placeholder="email">
            </div>
            <div class="control">
              <a class="button is-primary is-small">
                Search
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
}
</script>

<style lang="css" scoped>
</style>
