<template>
  <div class="min-h-screen bg-gray-90 text-gray-900">
    <!-- Hero Section -->
    <section class="bg-blue-600 text-white py-24">
      <div class="container mx-auto px-6 text-center">
        <h1 class="text-4xl md:text-6xl font-bold mb-4">Hi, I’m DC Breckle</h1>
        <p class="text-lg md:text-2xl mb-8">
          Full-stack developer building modern web apps with Vue, React, and more.
        </p>
        <router-link
          to="#projects"
          class="inline-block bg-white text-blue-600 font-semibold px-6 py-3 rounded shadow hover:bg-gray-100 transition"
        >
          View Projects
        </router-link>
      </div>
    </section>

    <!-- About Section -->
    <section class="py-24">
      <div class="container mx-auto px-6 md:flex md:items-center md:space-x-12">
        <!-- <img
          src="https://via.placeholder.com/300"
          alt="Profile"
          class="w-48 h-48 rounded-full mx-auto md:mx-0 mb-6 md:mb-0"
        /> -->
        <div class="text-center md:text-left">
          <h2 class="text-3xl font-bold mb-4">About Me</h2>
          <p class="text-gray-700 leading-relaxed mb-4">
            I’m a software engineer with experience in C++, C#, Java, JavaScript, and Vue/React. I
            love building clean, interactive web apps and learning new technologies.
          </p>
          <p class="text-gray-700 leading-relaxed">
            Currently, I focus on creating responsive full-stack projects and contributing to
            open-source tools.
          </p>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="bg-gray-100 py-24">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">Projects</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Pixel Painter</h3>
            <p class="text-gray-600 mb-4">
              A collaborative pixel art editor built with Vue 3 and WebSockets.
            </p>
            <a href="#" class="text-blue-600 font-semibold hover:underline"> View Project </a>
          </div>
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Tournament Bracket</h3>
            <p class="text-gray-600 mb-4">
              A web app to create, manage, and display tournament brackets.
            </p>
            <a href="#" class="text-blue-600 font-semibold hover:underline"> View Project </a>
          </div>
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Virufy Website</h3>
            <p class="text-gray-600 mb-4">
              Virufy.org is a non-profit using AI to detect COVID-19 from cough sounds. I am part of
              their web development team and helped build their site. our technologies include
              React, Tailwind CSS, and Next.js.
            </p>
            <a href="https://www.virufy.org/" class="text-blue-600 font-semibold hover:underline">
              View Project
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="py-24">
      <div class="container mx-auto px-6 text-center">
        <h2 class="text-3xl font-bold mb-4">Get In Touch</h2>
        <p class="text-gray-700 mb-6">
          Interested in working together or have a question? Reach out!
        </p>
        <a
          href="mailto:AngdroRyu@yahoo.com"
          class="inline-block bg-blue-600 text-white font-semibold px-6 py-3 rounded shadow hover:bg-blue-700 transition"
        >
          Email Me
        </a>
      </div>
    </section>
  </div>
</template>

<script setup>
// No script logic yet; purely static content for now
</script>

<style scoped>
/* You can add custom scoped styles here if needed */
</style>
