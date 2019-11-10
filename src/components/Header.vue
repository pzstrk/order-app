<template>
  <header>
    <nav>
      <a href="#" class="title">Order Online</a>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="#">Menu</a></li>
      </ul>
    </nav>
  </header>
</template>

<style>

header {
  padding: 20px;
  background-color: #5cb85c;
  color: #fff;
  box-shadow: 0px 2px 3px rgba(0,0,0,.4);
  margin-bottom: 20px;
}

header nav {
  display: flex;
}
header nav ul {
  list-style: none;
  display: flex;
  margin: 0;
  padding-left: 0;
}
header nav ul li a {
  padding: 0 .5rem;
}
header nav a {
  display: inline-block;
  text-decoration: none;
  color: inherit;
}
header nav a.title {
  text-transform: uppercase;
  font-weight: 700;
  margin-right: 1rem;
}
</style>
