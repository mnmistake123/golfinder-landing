<script>
export default {
  data() {
    return {
      deepLink: "", // The deep link will be dynamically set
    };
  },
  mounted() {
    // Get the query parameter from the URL
    const urlParams = new URLSearchParams(window.location.search);
    const id = urlParams.get("id"); // Extract the 'id' query parameter

    if (id) {
      // Construct the deep link dynamically
      this.deepLink = `golfinder.deep.com://details/${id}`;

      // Redirect to the deep link
      window.location.href = this.deepLink;

      // Optional: Add a fallback timeout to redirect to a web fallback URL
      setTimeout(() => {
        window.location.href = "fascinating-bubblegum-fcc5e4.netlify.app"; // Replace with your fallback URL
      }, 500); // Redirect to fallback after 0.5 seconds if the app doesn't open
    } else {
      console.error("No 'id' query parameter found in the URL.");
    }
  },
};
</script>

<template>
  <div class="redirect-container">
    <p class="redirect-message">
      Si no eres redirigido automáticamente,
      <a :href="deepLink" class="redirect-link">haz clic aquí</a>.
    </p>
  </div>
</template>

<style scoped>
.redirect-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh; /* Center vertically and horizontally */
  text-align: center;
  background-color: #f9fafb; /* Light background for better contrast */
}

.redirect-message {
  font-size: 1.5rem; /* Make the text larger */
  font-weight: bold; /* Add emphasis */
  color: #333; /* Darker text for readability */
}

.redirect-link {
  color: #14b8a6; /* Teal color for the link */
  text-decoration: underline;
  transition: color 0.3s ease;
}

.redirect-link:hover {
  color: #0d9488; /* Darker teal on hover */
}
</style>
