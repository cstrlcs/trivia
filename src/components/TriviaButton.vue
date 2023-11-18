<template>
  <button>
    <slot/>
  </button>
</template>

<style scoped>
button {
  display: block;
  width: 100%;
  background-color: #fff;
  border: 1px solid #000;
  border-radius: 4px;
  padding: 8px 16px;
  margin: 8px;
  font-size: 16px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

button:hover {
  transform: scale(1.1);
}
</style>
