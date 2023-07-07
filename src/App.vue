<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li>
            <router-link to="/weather" class="nav-link">
              <div class="component-box weather-box">Weather</div>
            </router-link>
          </li>
          <li>
            <router-link to="/location" class="nav-link">
              <div class="component-box location-box">Location</div>
            </router-link>
          </li>
          <li>
            <router-link to="/tictactoe" class="nav-link">
              <div class="component-box tictactoe-box">Tic Tac Toe</div>
            </router-link>
          </li>
          <li>
            <router-link to="/photo" class="nav-link">
              <div class="component-box photo-box">Photo</div>
            </router-link>
          </li>
          <li>
            <router-link to="/stopwatch" class="nav-link">
              <div class="component-box stopwatch-box">Stopwatch</div>
            </router-link>
          </li>
        </ul>
      </nav>
    </header>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  color: #333;
}

header {
  background: linear-gradient(135deg, #f64f59 0%, #c471ed 100%);
  padding: 20px;
}

nav ul {
  list-style: none;
  margin: 0;
  padding: 0;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-size: 1.5rem;
}

nav li {
  display: inline-block;
  margin-right: 10px;
}

nav a {
  font-weight: bold;
  color: #fff;
  text-decoration: none;
  padding: 5px 10px;
}

nav a.router-link-exact-active {
  color: #42b983;
}

nav a:hover {
  text-decoration: underline;
}

.component-box {
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 10px;
  background-color: #fff;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: background-color 0.3s ease;
  color: #333;
}

.component-box:hover {
  background-color: #f5f5f5;
}

.weather-box {
  background-color: #ff9800;
  color: #fff;
}

.location-box {
  background-color: #e91e63;
  color: #fff;
}

.stopwatch-box {
  background-color: #4caf50;
  color: #fff;
}

.tictactoe-box {
  background-color: #9c27b0;
  color: #fff;
}

.photo-box {
  background-color: #607d8b;
  color: #fff;
}

.nav-link {
  display: inline-block;
  margin-bottom: 10px;
}

.nav-link:last-child {
  margin-right: 0;
}
</style>
