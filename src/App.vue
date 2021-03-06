<template>
  <div id="app">
    <header class="header">
      <nav class="inner">
        <router-link to="/" exact>
          <img class="logo" src="~public/cityscapes-logo.svg" alt="logo">
        </router-link>
        <router-link to="/#products">Products</router-link>
        <router-link to="/brochures">Brochures</router-link>
        <router-link to="/gallery">Photo Gallery</router-link>
        <router-link to="/downloads">Revit / CAD</router-link>
        <router-link to="/help">Help &amp; Info</router-link>
        <router-link to="" class="menuBtn" @click.native="showMenu">&#9776;</router-link>
      </nav>
    </header>
    <div class="drawer">
      <router-link to="" class="menuBtn" @click.native="hideMenu">&nbsp;</router-link>
      <nav>
        <router-link to="/#products" @click.native="hideMenu">Products</router-link>
        <router-link to="/brochures" @click.native="hideMenu">Brochures</router-link>
        <router-link to="/gallery" @click.native="hideMenu">Photo Gallery</router-link>
        <router-link to="/downloads" @click.native="hideMenu">Revit / CAD</router-link>
        <router-link to="/help" @click.native="hideMenu">Help &amp; Info</router-link>
      </nav>
    </div>
    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
export default {
  name: "app",
  methods: {
    hideMenu: function() {
      document
        .getElementsByClassName("drawer")[0]
        .classList.remove("is-visible");
    },
    showMenu: function() {
      document.getElementsByClassName("drawer")[0].classList.add("is-visible");
    }
  }
};
</script>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500');
@import url('https://fonts.googleapis.com/icon?family=Material+Icons');
@import '../node_modules/vue-material/dist/vue-material.min.css';
@import '../node_modules/vue-material/dist/theme/black-green-light.css';

*, :before, :after {
  box-sizing: border-box;
}

html, html.md-theme-default {
  background: none !important;
  background-color: transparent;

  body {
    line-height: inherit;
  }

  a[href], a[href]:hover, a[href]:not(.md-button), a[href]:not(.md-button):hover {
    color: #34495e;
    text-decoration: none;
    cursor: pointer;
  }

  a.btn:not(.md-button) {
    display: inline-block;
    padding: 5px 8px;
    color: #fff;
    text-transform: uppercase;
    background: rgba(18, 49, 21, 0.7);
    border: 2px solid #fff;
    max-width: 250px;

    &:hover {
      color: #fff;
    }
  }

  h1, h2, h3, h4, h5, h6 {
    &, a:not(.md-button) {
      color: #076323;
    }
  }

  h1.angle-header, h1.angle-header a, h1.angle-header a:hover {
    color: white;
    text-decoration: none;
  }
}

h1, h2, h3, h4, h5, h6 {
  text-transform: uppercase;
  padding: 0;
  font-weight: normal;
}

body, html {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
  font-size: 18px;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
}

body {
  background-color: lighten(#eceef1, 30%);
  color: #34495e;
  overflow-y: scroll;
}

h1, h2 {
  text-align: center;
}

h1.angle-header {
  width: 100%;
  background: #076323;
  position: relative;
  padding-top: 50px;
  padding-bottom: 20px;
  z-index: 0;
  overflow: hidden;

  i, &:before, &:after {
    content: ' ';
    display: block;
    height: 100px;
    border-left: 600px solid transparent;
    border-right: 600px solid transparent;
    border-top: 20px solid #076323;
    position: absolute;
    left: 50%;
    margin-left: -600px;
    top: 100%;
    z-index: -1;
  }

  i {
    background: white;
    margin-top: -120px;
    border-left: 2000px solid transparent;
    border-right: 2000px solid transparent;
    margin-left: -2000px;
    border-top: 120px solid #076323;
    z-index: -2;
  }

  &:before {
    border-right: 700px solid transparent;
    margin-left: -610px;
    border-top: 40px solid #88A4B1;
    top: 0;
  }

  &:after {
    border-left: 700px solid transparent;
    margin-left: -700px;
    border-top: 30px solid white;
    top: -10px;
  }
}

h1 strong, h2 strong, h3 strong {
  font-weight: normal;
  border-top: 1px solid lightgray;
  border-bottom: 1px solid lightgray;
  display: inline-block;
  padding: 3px 20px;
  position: relative;

  &:before {
    content: ' ';
    border-left: 1px solid lightgray;
    height: 150%;
    position: absolute;
    left: 10px;
    top: -15%;
  }

  &:after {
    content: ' ';
    border-left: 1px solid lightgray;
    height: 150%;
    position: absolute;
    right: 10px;
    bottom: -15%;
  }
}

#app {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.is-visible ~ * {
  max-height: 100%;
  overflow: hidden;
}

.drawer ~ * {
  padding-top: 100px;
  flex-basis: 100%;
}

.header {
  background-color: white;
  position: fixed;
  z-index: 999;
  height: 92px;
  top: 0;
  left: 0;
  right: 0;

  .inner {
    box-sizing: border-box;
    margin: 0px auto;
    padding: 15px 5px;
  }

  a {
    color: #0B5E24;
    line-height: 24px;
    transition: color 0.15s ease;
    display: inline-block;
    vertical-align: middle;
    font-weight: 300;
    letter-spacing: 0.075em;
    margin-right: 1.8em;

    &:hover {
      color: #0B5E24;
    }

    &.router-link-active {
      color: #0B5E24;
      font-weight: 400;
    }

    &:nth-child(6) {
      margin-right: 0;
    }
  }

  .menuBtn {
    display: none;
    float: right;
    font-size: 30px;
    margin: 20px 0;
  }
}

.drawer {
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  position: fixed;
  overflow: hidden;
  visibility: hidden;

  &.is-visible {
    visibility: visible;
  }

  &.is-visible nav {
    width: 200px;
  }

  nav {
    white-space: nowrap;
    width: 0;
    height: 100%;
    background-color: white;
    transition: ease-in-out 0.15s;
  }

  a {
    display: block;
    padding: 10px 20px;
  }

  a:hover:not(.menuBtn) {
    background-color: rgba(0, 0, 0, 0.2);
  }

  .menuBtn {
    background-color: rgba(0, 0, 0, 0.5);
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    z-index: -1;
  }
}

.logo {
  width: 200px;
  margin-right: 10px;
  display: inline-block;
  vertical-align: middle;
}

.view {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
  width: 100%;
}

.fade-enter-active, .fade-leave-active {
  transition: all 0.2s ease;
}

.fade-enter, .fade-leave-active {
  opacity: 0;
}

@media (max-width: 1000px) {
  .header {
    .menuBtn {
      display: inline-block;
    }

    a:not(:first-of-type):not(:last-of-type) {
      display: none;
    }

    .github {
      display: none;
    }
  }
}

@media (max-width: 500px) {
  body, html {
    font-size: 16px;
  }
}

@media (max-height: 500px) {
  body, html {
    font-size: 16px;
  }

  .drawer ~ * {
    padding-top: 65px;
  }

  .header {
    height: 65px;

    .inner {
      padding: 0 5px;
    }
  }
}
</style>
