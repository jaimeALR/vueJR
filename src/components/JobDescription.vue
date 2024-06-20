<template>
  <div class="backdrop">
    <div class="JobDescription">
      <h2>{{ header }}</h2>
      <p>Job Description content</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["header"],
};
</script>
<style >
.JobDescription {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background-color: white;
  border-radius: 10px;
}

.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5); /* Black with 50% opacity */
  z-index: 2; /* Ensure the backdrop is behind the modal */
}
</style>