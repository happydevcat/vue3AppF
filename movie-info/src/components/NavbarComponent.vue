<template>
  <nav>
      <a href="#">Home</a>
      <a href="#">Movie</a>
      <a href="#">About</a>
  </nav>
</template>

<script >
export default {
  
  name: 'NavbarComponent',
}
</script>

<style scoped>

nav {
  background-color: #f0f8ff;
  padding: 10px;
  border-radius: 8px;
  display: flex;
  gap: 15px;
  justify-content: center;
}

a {
  text-decoration: none;
  color: #333;
  font-weight: bold;
  transition: 0.3s;
}

a:hover {
  color: #0077cc;
}
</style>
