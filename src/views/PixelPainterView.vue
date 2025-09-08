<template>
  <div class="min-h-screen bg-gray-90 text-gray-900">
    <!-- Hero Section -->
    <section class="bg-pink-500 text-white py-24">
      <div class="container mx-auto px-6 text-center">
        <h1 class="text-4xl md:text-6xl font-bold mb-4">Pixel Painter</h1>
        <p class="text-lg md:text-2xl mb-8">
          A somewhat minimalistic pixel art painting software build with Vue 3 and node.js frontend
          with a .Net and c# backend.
        </p>
        <a
          href="https://github.com/GranquistR/Pixel-Painter"
          class="inline-block m-1 bg-white text-blue-600 font-semibold px-6 py-3 rounded shadow hover:bg-gray-100 transition"
          target="_blank"
          rel="noopener noreferrer"
        >
          View Verison 1.0 Repo
        </a>
        <a
          href="https://github.com/sucha3162/Pixel-Painter-2.0"
          class="m-1 inline-block bg-white text-blue-600 font-semibold px-6 py-3 rounded shadow hover:bg-gray-100 transition"
          target="_blank"
          rel="noopener noreferrer"
        >
          View Verison 2.0 Repo
        </a>
      </div>
    </section>
    <div class="flex justify-center items-center mt-10">
      <div class="flex justify-center items-center border-4 shadow-8">
        <my-canvas v-model="squareColor" :art="art" :pixelSize="10" :canvasNumber="1" />
      </div>
    </div>
    <div>
      <div class="container mx-auto px-6 text-center block mt-12 mb-4">
        <button
          @click="greyScaleFilter"
          class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          :class="greyscale ? 'bg-pink-500 hover:bg-pink-600' : 'bg-blue-600 hover:bg-blue-700'"
        >
          Apply Grayscale Filter
        </button>

        <button
          @click="sepiaFilter"
          class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          :class="sepia ? 'bg-pink-500 hover:bg-pink-600' : 'bg-blue-600 hover:bg-blue-700'"
        >
          Apply Sepia Filter
        </button>

        <button
          @click="protanopeFilter"
          class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          :class="prota ? 'bg-pink-500 hover:bg-pink-600' : 'bg-blue-600 hover:bg-blue-700'"
        >
          Apply Protanope Filter
        </button>
        <button
          @click="deuFilter"
          class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          :class="deu ? 'bg-pink-500 hover:bg-pink-600' : 'bg-blue-600 hover:bg-blue-700'"
        >
          Apply Deuteranope Filter
        </button>
        <button
          class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          @click="showTones = !showTones"
          :class="duotone ? 'bg-pink-500 hover:bg-pink-600' : 'bg-blue-600 hover:bg-blue-700'"
        >
          DuoTone
        </button>

        <div v-show="showTones" class="container mx-auto py-1 px-6 text-center md:flex">
          <h4 class="m-auto">Color 1</h4>
          <h4 class="m-auto">{{ toneOne }}</h4>
          <input
            type="color"
            id="tone1"
            v-model="toneOne"
            class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          />
          <h4 class="m-auto">Color 2</h4>
          <h4 class="m-auto p-auto">{{ toneTwo }}</h4>
          <input
            type="color"
            id="tone2"
            v-model="toneTwo"
            class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
          />
          <button
            class="ml-4 bg-blue-600 text-white font-semibold px-4 py-2 rounded shadow hover:bg-blue-700 transition"
            :severity="duotone ? 'primary' : 'secondary'"
            @click="duoToneFilter(toneOne, toneTwo)"
          >
            Generate
          </button>
        </div>
      </div>
    </div>
    <!-- About Section -->
    <section class="py-24">
      <div class="container mx-auto px-6 md:flex md:items-center md:space-x-12">
        <!-- <img
          src="https://via.placeholder.com/300"
          alt="Profile"
          class="w-48 h-48 rounded-full mx-auto md:mx-0 mb-6 md:mb-0"
        /> -->
        <div class="text-center md:text-left">
          <h2 class="text-3xl font-bold mb-4">About the Project</h2>
          <p class="text-gray-700 leading-relaxed mb-4">
            Pixel Painter is a collaborative pixel art editor with many social media elements.
            Artists can create their own pixel art in the canvas and save it to share with others.
            You can like and comment on other people's art. The front-end was a Vue.js 3 with
            typescript with primeflex for styling and pixi.js for the graphical library used while
            drawing. The back-end was built with .Net 6 and C#. The database used was a Microsoft
            SQL server.
          </p>
          <p class="text-gray-700 leading-relaxed mb-4">
            Version 1.0 was the first version of the project that was built by Ryan Granquist, Alex
            Such, Riley Dummer, John Nicpon, Jacob Sletten and myself. The focus for version 1.0 was
            getting the project up and running with the basic features of a pixel art editor with
            social media elements. We used Google Oauth for secure login, so we did not have to hold
            on to sensitive information like someone’s password, instead we only had to store the
            user identifier. The pixi.js library was used to generate canvases as well as any paint
            that went on the canvas. The drawing functions were done in typescript, when the user
            was done drawing they could save their art to the database. The art in the gallery was
            displayed using a canvas element to reduce the load with pixi.js. With Microsoft SQL
            server we were able to store the art as a string of hex values that made it easy to
            store and retrieve, we also stored the title of the art, who the artist is, the size of
            the art in pixels, and the date the art was made. Triggers were used to optimize the
            database usage, when someone deletes a comment on a piece of art, any additional replies
            on the comment were then deleted, and when a user deleted their account all comments,
            likes, and art were deleted as well. Testing for the project was done with Docker and
            when we were ready to deploy, we used nginx and Digital Ocean to host the project.
          </p>
          <p class="text-gray-700 leading-relaxed mb-4">
            Version 2.0 our group consisted of Alex Such, Riley Dummer, Aidan Drew, Helmrick Jordan,
            Jacob Sletten and myself. The main focus for version 2.0 was to improve the user
            experience and add more features to the pixel art editor. The main goals for the 2.0
            release were: for multiple artists to be able to work on the same art piece both
            synchronously and asynchronously, the ability to add filters on art, and administration
            privileges for the site since they were not added before. To add the ability for
            multiple artists to collaborate, we needed to rework our database schema since the
            artist was stored on the art piece, now with the addition on the ContributingArtist
            table we were able to make that work, although it required the rework of many of the
            CRUD functionality. While working on the filters for the art, i.e. grayscale, duotone,
            sepia, one of the members of our group, had suggested that we add the ability to make a
            filter for colorblind people to use to see the art better. Having found some research
            papers containing formulas to turn LMS color into colorblind friendly colors, I had made
            the calculations necessary to turn our hex valued colors into rgb then into lms to do
            the calculations to turn it into both deuteranope friendly and protanope friendly
            colors. Above is an example of one of our art pieces with the filter’s buttons enabled,
            so you can try it for yourself.
          </p>
        </div>
      </div>
    </section>
  </div>

  <div class="m-5"></div>
</template>
<script setup lang="ts">
import MyCanvas from '@/components/MyCanvas.vue'
import { ref } from 'vue'
const showFilters = ref<boolean>(false)
const showTones = ref<boolean>(false)
const squareColor = ref<string>('blue')
const toneOne = ref<string>('#ff0000')
const toneTwo = ref<string>('#0000ff')
//filters
const greyscale = ref<boolean>(false)
const filtered = ref<boolean>(false)
const duotone = ref<boolean>(false)
const sepia = ref<boolean>(false)
const prota = ref<boolean>(false)
const hover = ref<boolean>(false)
const deu = ref<boolean>(false)

function testcolor(): void {
  console.log(art.value.pixelGrid.encodedGrid)
}

const art = ref<Art>({
  width: 8,
  height: 8,
  data: [],
  pixelGrid: {
    width: 32,
    height: 32,
    grid: Array(16)
      .fill(undefined)
      .map(() => Array(16).fill('#ffffff')),
    encodedGrid:
      'FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5edFFFFFF9cd5ed9cd5ed73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5edFFFFFFFFFFFF9cd5ed9cd5ed73523e73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed73523e73523e73523e73523e73523e73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed73523e73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed73523e73523e9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed84c3e084c3e084c3e0FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF84c3e084c3e084c3e084c3e084c3e084c3e022B14C22B14C22B14C22B14C9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed9cd5ed',
  },
})
interface Art {
  width: number
  height: number
  data: string[]
  isGif?: boolean
  pixelGrid: {
    width: number
    height: number
    grid: string[][]
    encodedGrid?: string
  }
}
const copyArt = ref<string[]>([])
copyArt.value.push(art.value.pixelGrid.encodedGrid!)

function greyScaleFilter(): void {
  if (filtered.value && greyscale.value) {
    resetFilters()
  } else {
    resetFilters()
    if (art.value.pixelGrid.encodedGrid)
      squareColor.value = filterGreyScale(art.value.pixelGrid.encodedGrid!)
    filtered.value = true
    greyscale.value = true
  }
}

function hexToRGB(hex: string): number[] {
  let rgb: number[] = []
  let r = parseInt(hex.slice(0, 2), 16),
    g = parseInt(hex.slice(2, 4), 16),
    b = parseInt(hex.slice(4, 6), 16)

  rgb[0] = r
  rgb[1] = g
  rgb[2] = b

  return rgb
}
function rgbToHex(r: number, g: number, b: number) {
  return [Math.round(r), Math.round(g), Math.round(b)]
    .map((x) => {
      const hex = x.toString(16)
      return hex.length === 1 ? '0' + hex : hex
    })
    .join('')
}
function rgbToGrayscale(red: number, green: number, blue: number) {
  let r = red * 0.3 // ------> Red is low
  let g = green * 0.59 // ---> Green is high
  let b = blue * 0.11 // ----> Blue is very low
  r = Math.round(r)
  g = Math.round(g)
  b = Math.round(b)

  var gray = r + g + b

  return [gray, gray, gray]
}

function filterGreyScale(currentGrid: string): string {
  let newGrid: string = ''
  let currentcolorrgb: number[] = []
  let newrgb: number[] = []
  let newhexcolor: string = ''
  for (var i = 0; i <= currentGrid.length - 6; i += 6) {
    var currentcolor = currentGrid.substring(i, i + 6)
    currentcolorrgb = hexToRGB(currentcolor)
    newrgb = rgbToGrayscale(currentcolorrgb[0], currentcolorrgb[1], currentcolorrgb[2])
    newhexcolor = rgbToHex(newrgb[0], newrgb[1], newrgb[2])
    newGrid += newhexcolor
  }
  return newGrid
}
function resetFilters(): void {
  filtered.value = false
  greyscale.value = false
  duotone.value = false
  prota.value = false
  deu.value = false
  sepia.value = false

  if (art.value.pixelGrid.encodedGrid) {
    art.value.pixelGrid.encodedGrid = copyArt.value[0]
    squareColor.value = art.value.pixelGrid.encodedGrid
  }
}

function generateGradient(toneOne: string, toneTwo: string): number[] {
  let rgb1: number[] = hexToRGB(toneOne.substring(1, 7))
  let rgb2: number[] = hexToRGB(toneTwo.substring(1, 7))
  let gradient: number[] = []
  for (var i = 0; i < 256 * 3; i += 3) {
    gradient[i] = Math.round(((256 - i / 4) * rgb1[0] + (i / 4) * rgb2[0]) / 256)
    gradient[i + 1] = Math.round(((256 - i / 4) * rgb1[1] + (i / 4) * rgb2[1]) / 256)
    gradient[i + 2] = Math.round(((256 - i / 4) * rgb1[2] + (i / 4) * rgb2[2]) / 256)
  }
  return gradient
}
function duoTone(currentGrid: string, toneOne: string, toneTwo: string): string {
  let j = 0
  let newGrid: string = ''
  let gradient: number[] = generateGradient(toneOne, toneTwo)
  let gradientGrid: number[][] = []
  currentGrid = filterGreyScale(currentGrid)
  for (let i = 0; i <= currentGrid.length - 6; i += 6) {
    gradientGrid[j] = hexToRGB(currentGrid.substring(i, i + 6))
    j++
  }
  for (var k = 0; k < gradientGrid.length; k++) {
    let r = gradientGrid[k][0]
    let g = gradientGrid[k][1]
    let b = gradientGrid[k][2]
    let brightness = Math.round(r * 0.2126 + g * 0.7152 + b * 0.0722)
    gradientGrid[k][0] = gradient[brightness * 3]
    gradientGrid[k][1] = gradient[brightness * 3 + 1]
    gradientGrid[k][2] = gradient[brightness * 3 + 2]
    newGrid += rgbToHex(gradientGrid[k][0], gradientGrid[k][1], gradientGrid[k][2])
  }
  return newGrid
}
function duoToneFilter(toneOne: string, toneTwo: string): void {
  if (filtered.value && duotone.value) {
    resetFilters()
  } else {
    resetFilters()
    squareColor.value = duoTone(art.value.pixelGrid.encodedGrid!, toneOne, toneTwo)
    filtered.value = true
    duotone.value = true
  }
}
function sepiaTone(R: number, G: number, B: number): number[] {
  let newColors: number[] = []
  let newRed = Math.round(0.393 * R + 0.769 * G + 0.189 * B)
  if (newRed > 255) newRed = 255
  let newGreen = Math.round(0.349 * R + 0.686 * G + 0.168 * B)
  if (newGreen > 255) newGreen = 255
  let newBlue = Math.round(0.272 * R + 0.534 * G + 0.131 * B)
  if (newBlue > 255) newBlue = 255
  newColors[0] = newRed
  newColors[1] = newGreen
  newColors[2] = newBlue

  return newColors
}
function filterSepia(currentGrid: string): string {
  let newGrid: string = ''
  let currentcolorrgb: number[] = []
  let newrgb: number[] = []
  let newhexcolor: string = ''
  for (var i = 0; i <= currentGrid.length - 6; i += 6) {
    var currentcolor = currentGrid.substring(i, i + 6)
    currentcolorrgb = hexToRGB(currentcolor)
    newrgb = rgbToGrayscale(currentcolorrgb[0], currentcolorrgb[1], currentcolorrgb[2])
    newrgb = sepiaTone(newrgb[0], newrgb[1], newrgb[2])
    newhexcolor = rgbToHex(newrgb[0], newrgb[1], newrgb[2])
    newGrid += newhexcolor
  }
  return newGrid
}
function sepiaFilter(): void {
  if (filtered.value && sepia.value) {
    resetFilters()
  } else {
    resetFilters()
    squareColor.value = filterSepia(art.value.pixelGrid.encodedGrid!)
    filtered.value = true
    sepia.value = true
  }
}
function gammaCorrection(OldColor: number): number {
  let NewColor = (OldColor / 255) ** 2.2
  return NewColor
}
function inverseGammaCorrection(OldColor: number): number {
  if (OldColor < 0) {
    Math.abs(OldColor)
  }
  let expo = 1 / 2.2
  let NewColor = Math.pow(OldColor, expo)
  NewColor = NewColor * 255
  if (NewColor > 255) {
    NewColor = 255
  }
  return NewColor
}
function rgbToLMS(rgbcolors: number[]): number[][] {
  let newrgbcolors: number[][] = [[], [], []]
  newrgbcolors[0][0] = rgbcolors[0]
  newrgbcolors[1][0] = rgbcolors[1]
  newrgbcolors[2][0] = rgbcolors[2]

  let LMSColors: number[][] = []
  const LMSCalc: number[][] = [
    [17.8824, 43.5161, 4.11935],
    [3.45565, 27.1554, 3.86714],
    [0.0299566, 0.184309, 1.46709],
  ]
  var LMScolumns = LMSCalc[0].length
  var LMSRows = LMSCalc.length
  var RGBcolumns = newrgbcolors[0].length
  for (let i = 0; i < LMSRows; i++) {
    LMSColors[i] = []
    for (let j = 0; j < RGBcolumns; j++) {
      let sum = 0
      for (let k = 0; k < LMScolumns; k++) {
        sum += LMSCalc[i][k] * newrgbcolors[k][j]
      }
      LMSColors[i][j] = sum
    }
  }
  return LMSColors
}
function lmsToProtanopes(LMScolors: number[][]): number[][] {
  let ProtanopeColors: number[][] = []
  const ProtanopeCalc: number[][] = [
    [0, 2.02344, -2.52581],
    [0, 1, 0],
    [0, 0, 1],
  ]
  let PTPcolumns = ProtanopeCalc[0].length
  let PTPRows = ProtanopeCalc.length
  let LMScolumns = LMScolors[0].length
  for (let i = 0; i < PTPRows; i++) {
    ProtanopeColors[i] = []
    for (let j = 0; j < LMScolumns; j++) {
      let sum = 0
      for (let k = 0; k < PTPcolumns; k++) {
        sum += ProtanopeCalc[i][k] * LMScolors[k][j]
      }
      ProtanopeColors[i][j] = sum
    }
  }

  return ProtanopeColors
}
function lmsToDeuteranopes(LMScolors: number[][]): number[][] {
  let DeuteranopesColors: number[][] = []
  const DeuteranopesCalc: number[][] = [
    [1, 0, 0],
    [0.494207, 0, 1.24827],
    [0, 0, 1],
  ]
  let DEUcolumns = DeuteranopesCalc[0].length
  let DEURows = DeuteranopesCalc.length
  let LMScolumns = LMScolors[0].length
  for (let i = 0; i < DEURows; i++) {
    DeuteranopesColors[i] = []
    for (let j = 0; j < LMScolumns; j++) {
      let sum = 0
      for (let k = 0; k < DEUcolumns; k++) {
        sum += DeuteranopesCalc[i][k] * LMScolors[k][j]
      }
      DeuteranopesColors[i][j] = sum
    }
  }

  return DeuteranopesColors
}
function lmsToRGB(LMScolors: number[][]): number[] {
  let RGBcolors: number[][] = []
  let reformatedcolors: number[] = []
  const RGBCal: number[][] = [
    [0.080944, -0.130504, 0.116721],
    [-0.0102485, 0.0540194, -0.113615],
    [-0.000365294, -0.00412163, 0.693513],
  ]
  let LMScolumns = LMScolors[0].length
  let RGBRows = RGBCal.length
  let RGBcolumns = RGBCal.length

  for (let i = 0; i < RGBRows; i++) {
    RGBcolors[i] = []
    for (let j = 0; j < LMScolumns; j++) {
      let sum = 0
      for (let k = 0; k < RGBcolumns; k++) {
        sum += RGBCal[i][k] * LMScolors[k][j]
      }
      if (sum < 0) sum = 0
      RGBcolors[i][j] = sum
    }
  }
  reformatedcolors[0] = RGBcolors[0][0]
  reformatedcolors[1] = RGBcolors[1][0]
  reformatedcolors[2] = RGBcolors[2][0]
  return reformatedcolors
}

/*
 Calculations made from:
Digital Video Colourmaps for
Checking the Legibility of
Displays by Dichromats
Francoise Vie�not,Hans Brettel,John D. Mollon

https://vision.psychol.cam.ac.uk/jdmollon/papers/colourmaps.pdf
*/

function filterProtanope(currentGrid: string): string {
  let newGrid: string = ''
  let currentcolorrgb: number[] = []
  let currentcolorlms: number[][] = []
  let newcolorlms: number[][] = []
  let newrgb: number[] = []
  let newhexcolor: string = ''
  for (var i = 0; i <= currentGrid.length - 6; i += 6) {
    var currentcolor = currentGrid.substring(i, i + 6)
    currentcolorrgb = hexToRGB(currentcolor)
    currentcolorrgb = [
      gammaCorrection(currentcolorrgb[0]),
      gammaCorrection(currentcolorrgb[1]),
      gammaCorrection(currentcolorrgb[2]),
    ]

    //after gamma adjustment
    currentcolorrgb[0] = 0.992052 * currentcolorrgb[0] + 0.003974
    currentcolorrgb[1] = 0.992052 * currentcolorrgb[1] + 0.003974
    currentcolorrgb[2] = 0.992052 * currentcolorrgb[2] + 0.003974

    currentcolorlms = rgbToLMS(currentcolorrgb)
    newcolorlms = lmsToProtanopes(currentcolorlms)
    newrgb = lmsToRGB(newcolorlms)
    newrgb = [
      inverseGammaCorrection(newrgb[0]),
      inverseGammaCorrection(newrgb[1]),
      inverseGammaCorrection(newrgb[2]),
    ]
    newhexcolor = rgbToHex(newrgb[0], newrgb[1], newrgb[2])
    newGrid += newhexcolor
  }
  return newGrid
}
function protanopeFilter(): void {
  if (filtered.value && prota.value) {
    resetFilters()
  } else {
    resetFilters()
    squareColor.value = filterProtanope(art.value.pixelGrid.encodedGrid!)
    filtered.value = true
    prota.value = true
  }
}
function filterDeu(currentGrid: string): string {
  let newGrid: string = ''
  let currentcolorrgb: number[] = []
  let currentcolorlms: number[][] = []
  let newcolorlms: number[][] = []
  let newrgb: number[] = []
  let newhexcolor: string = ''
  for (var i = 0; i <= currentGrid.length - 6; i += 6) {
    var currentcolor = currentGrid.substring(i, i + 6)
    currentcolorrgb = hexToRGB(currentcolor)
    currentcolorrgb = [
      gammaCorrection(currentcolorrgb[0]),
      gammaCorrection(currentcolorrgb[1]),
      gammaCorrection(currentcolorrgb[2]),
    ]
    //after gamma adjustment Deu
    currentcolorrgb[0] = 0.957237 * currentcolorrgb[0] + 0.0213814
    currentcolorrgb[1] = 0.957237 * currentcolorrgb[1] + 0.0213814
    currentcolorrgb[2] = 0.957237 * currentcolorrgb[2] + 0.0213814

    currentcolorlms = rgbToLMS(currentcolorrgb)
    newcolorlms = lmsToDeuteranopes(currentcolorlms)
    newrgb = lmsToRGB(newcolorlms)
    newrgb = [
      inverseGammaCorrection(newrgb[0]),
      inverseGammaCorrection(newrgb[1]),
      inverseGammaCorrection(newrgb[2]),
    ]
    newhexcolor = rgbToHex(newrgb[0], newrgb[1], newrgb[2])
    if (newhexcolor.length != 6) {
      console.error(`Found it! (${i}): ${newhexcolor}`)
    }
    newGrid += newhexcolor
  }
  return newGrid
}
function deuFilter(): void {
  if (filtered.value && deu.value) {
    resetFilters()
  } else {
    resetFilters()
    squareColor.value = filterDeu(art.value.pixelGrid.encodedGrid!)
    filtered.value = true
    deu.value = true
  }
}
</script>
