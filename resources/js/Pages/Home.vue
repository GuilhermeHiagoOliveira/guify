<script setup>
import BaseLayout from "@/Layouts/BaseLayout.vue";
import { Head } from "@inertiajs/inertia-vue3";

const list = [
  {
    name: "Rockeira",
    file: "music1.mp3",
    image: "nyan-cat-1.gif",
    actor: "Grupo do ROCK Mané",
  },
  {
    name: "Eletroniqueira",
    file: "music2.mp3",
    image: "cz-logo.webp",
    actor: "Tuts tuts quero ver",
  },
];
</script>

<template>
  <Head title="Guify" />

  <BaseLayout v-slot="scope">
    <div class="first-music-section">
      <h2 class="mb-4"><b>Bom dia</b></h2>
      <div class="first-music-section-card">
        <div>
          <span class="likeSongs-card">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              height="38"
              width="38"
              viewBox="0 0 48 48"
            >
              <path
                d="m24 41.95-2.05-1.85q-5.3-4.85-8.75-8.375-3.45-3.525-5.5-6.3T4.825 20.4Q4 18.15 4 15.85q0-4.5 3.025-7.525Q10.05 5.3 14.5 5.3q2.85 0 5.275 1.35Q22.2 8 24 10.55q2.1-2.7 4.45-3.975T33.5 5.3q4.45 0 7.475 3.025Q44 11.35 44 15.85q0 2.3-.825 4.55T40.3 25.425q-2.05 2.775-5.5 6.3T26.05 40.1Z"
              />
            </svg>
          </span>
          <label>Músicas Curtidas</label>
          <span class="play-button">
            <button aria-label="Play" @click="scope.playSong('teste2')">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div>
        <div>
          <img src="img/nyan-cat-1.gif" alt="" />
          <label>Pagodeira</label>
          <span class="play-button">
            <button aria-label="Play" @click="playSong(this)">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div>
        <div>
          <img src="img/nyan-cat-1.gif" alt="" />
          <label>Funkeira</label>
          <span class="play-button">
            <button aria-label="Play" @click="playSong(this)">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div>
        <div>
          <img src="img/nyan-cat-1.gif" alt="" />
          <label>Sertanejeira</label>
          <span class="play-button">
            <button aria-label="Play" @click="playSong(this)">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div>
        <div v-for="l in list" :key="l">
          <img :src="'img/' + l.image" alt="" />
          <label>{{ l.name }}</label>
          <span class="play-button">
            <button aria-label="Play" @click="scope.playSong(l.file)">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div>
        <!-- <div>
          <img src="img/nyan-cat-1.gif" alt="" />
          <label>Eletroniqueira</label>
          <span class="play-button">
            <button aria-label="Play" @click="playSong(this)">
              <span
                ><span>
                  <svg role="img" height="24" width="24" viewBox="0 0 24 24">
                    <path
                      d="M7.05 3.606l13.49 7.788a.7.7 0 010 1.212L7.05 20.394A.7.7 0 016 19.788V4.212a.7.7 0 011.05-.606z"
                    ></path>
                  </svg>
                </span>
              </span>
            </button>
          </span>
        </div> -->
      </div>
    </div>
  </BaseLayout>
</template>
