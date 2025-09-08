<template>
  <div class="min-h-screen bg-gray-90 text-gray-900">
    <!-- Hero Section -->
    <section class="bg-blue-600 text-white py-24">
      <div class="container mx-auto px-6 text-center">
        <h1 class="text-4xl md:text-6xl font-bold mb-4">Hi, I’m DC Breckle</h1>
        <p class="text-lg md:text-2xl mb-8">
          Full-stack developer building modern web apps with Vue, React, and more.
        </p>
        <button
          class="inline-block bg-white text-blue-600 font-semibold px-6 py-3 rounded shadow hover:bg-gray-100 transition"
          @click="scrollToSection"
        >
          View Projects
        </button>
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
            I’m a software engineer with experience in front-end (Vue, React, JavaScript,
            TypeScript), back-end (Node.js, .Net, C#, Rust, C++, Java), and Databases (MySQL,
            Microsoft SQL server)
          </p>
          <p class="text-gray-700 leading-relaxed">
            Currently, I focus on creating responsive full-stack projects and improving my
            programming knowledge
          </p>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section ref="projects" class="bg-gray-100 py-24">
      <div class="container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">Projects</h2>
        <div class="grid md:grid-cols-3 gap-8">
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Pixel Painter</h3>
            <p class="text-gray-600 mb-4">
              A somewhat minimalistic pixel art painting software build with Vue 3 and node.js
              frontend with a .Net and c# backend.
            </p>
            <router-link to="/PixelPainter" class="text-blue-600 font-semibold hover:underline">
              View Project
            </router-link>
          </div>
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Virufy Website</h3>
            <p class="text-gray-600 mb-4">
              Virufy.org is a non-profit using AI to detect COVID-19 from cough sounds. I am part of
              their web development team and helped build their site. Our technologies include
              React, Tailwind CSS, and Next.js.
            </p>
            <a href="https://www.virufy.org/" class="text-blue-600 font-semibold hover:underline">
              View Project
            </a>
          </div>
          <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
            <h3 class="text-xl font-semibold mb-2">Pharmacy Mock-up</h3>
            <p class="text-gray-600 mb-4">
              A web app to mimic the layout and functionalliy of a pharmacy system made with Vue,
              Node.js, Rust and Microsoft SQL Server. Currently Work in Progress!!!
            </p>
            <a
              href="https://github.com/AngdroRyu/phar"
              class="text-blue-600 font-semibold hover:underline"
            >
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
import { ref } from 'vue'

const projects = ref(null)

function scrollToSection() {
  projects.value?.scrollIntoView({ behavior: 'smooth' })
}
</script>
