<script>
export default {
  data() {
    return {
      deepLink: "", // The deep link will be dynamically set
      fallbackUrl: "https://fascinating-bubblegum-fcc5e4.netlify.app", // Web fallback URL
      appDownloadUrl: "https://example.com/download", // Replace with your app's download page URL
      showInstructions: false, // Show instructions after redirect attempt
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

      // Add a fallback timeout to redirect to the app download page
      setTimeout(() => {
        if (!document.hidden) {
          // If the app doesn't open, redirect to the app download page
          window.location.href = this.appDownloadUrl; // Redirect to the app download page
        }
      }, 1500); // Redirect to download page after 1.5 seconds if the app doesn't open
    } else {
      console.error("No 'id' query parameter found in the URL.");
      // Redirect to the fallback URL if no ID is found
      window.location.href = this.fallbackUrl;
    }
  },
};
</script>

<template>
  <div class="redirect-container">
    <div v-if="!showInstructions">
      <p class="redirect-message">
        Si no eres redirigido automáticamente,
        <a :href="deepLink" class="redirect-link">haz clic aquí</a>.
        <br />
        ¿No tienes la app?
        <a :href="appDownloadUrl" class="download-link">Descárgala aquí</a>.
      </p>
    </div>
    <div v-else>
      <p class="instructions-message">
        Instala la app y luego abre el siguiente enlace para continuar:
        <br />
        <a :href="deepLink" class="deep-link">Abrir enlace</a>.
      </p>
    </div>
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
  padding: 1rem;
}

.redirect-message,
.instructions-message {
  font-size: 1.5rem; /* Make the text larger */
  font-weight: bold; /* Add emphasis */
  color: #333; /* Darker text for readability */
}

.redirect-link,
.download-link,
.deep-link {
  color: #14b8a6; /* Teal color for the link */
  text-decoration: underline;
  transition: color 0.3s ease;
}

.redirect-link:hover,
.download-link:hover,
.deep-link:hover {
  color: #0d9488; /* Darker teal on hover */
}
</style>
