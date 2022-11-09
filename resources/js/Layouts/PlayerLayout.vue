<script setup>
import { ref, onMounted, watch, reactive } from "vue";

// Player Title Move -----------------------------------------------------------

const xPosition = ref(0);
const status = ref("");
const textDirection = ref("");

function changeStatus(st) {
  status.value = st;
  var calc = -(
    document.getElementById("player-label-music-title").offsetWidth -
    document.getElementsByClassName("player-actual-music-infos")[0].offsetWidth
  );
  const myInterval = window.setInterval(function () {
    if (status.value == "leaved") {
      if (calc < 0 && (xPosition.value > calc || xPosition.value >= 0)) {
        if (textDirection.value == "") {
          textDirection.value = "right";
        }
        titleMove(calc);
      } else if (xPosition.value < 0) {
        if (textDirection.value == "") {
          textDirection.value = "left";
        }
        titleMove(calc);
      }
    } else if (status.value == "standing") {
      clearInterval(myInterval);
    }
  }, 60);
  if (st == "standing") {
    clearInterval(myInterval);
  }
}

function titleMove(calc) {
  if (textDirection.value === "left") {
    xPosition.value += 0.4;
    if (xPosition.value >= 0 || xPosition.value <= calc) {
      textDirection.value = "";
    }
  } else if (textDirection.value === "right") {
    xPosition.value -= 0.4;
    if (xPosition.value >= 0 || xPosition.value <= calc) {
      textDirection.value = "";
    }
  }
  document.documentElement.style.setProperty(
    "--trans-x",
    xPosition.value + "px"
  );
}

// End Player title Move --------------------------------------------------------

const suffleBtn = ref("suffleBtn");
const backBtn = ref("backBtn");
const playPauseBtn = ref("playPauseBtn");
const nextBtn = ref("nextBtn");
const repeatBtn = ref("suffleBtn");

const props = defineProps(['song', 'loaded', 'track']);



</script>

<template>
  <div class="player-bar">
    <div class="player-actual-music">
      <div class="player-actual-music-image">
        <img v-if="props.song" :src="'img/'+props.song.image" alt="" />
      </div>
      <div class="player-actual-music-infos">
        <div class="player-actual-music-title">
          <div>
            <label
              id="player-label-music-title"
              @mouseover="changeStatus('standing')"
              @mouseleave="changeStatus('leaved')"
              >{{props.song?props.song.title:''}}</label
            >
          </div>
        </div>
        <div class="player-actual-music-singer">
          <label>{{props.song?props.song.actor:''}}</label>
        </div>
      </div>
    </div>
    <div class="player-controller">
        <div class="player-controller-top">
            <button @click="$emit('suffleClick')" ref="suffleBtn">
                <svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M13.151.922a.75.75 0 10-1.06 1.06L13.109 3H11.16a3.75 3.75 0 00-2.873 1.34l-6.173 7.356A2.25 2.25 0 01.39 12.5H0V14h.391a3.75 3.75 0 002.873-1.34l6.173-7.356a2.25 2.25 0 011.724-.804h1.947l-1.017 1.018a.75.75 0 001.06 1.06L15.98 3.75 13.15.922zM.391 3.5H0V2h.391c1.109 0 2.16.49 2.873 1.34L4.89 5.277l-.979 1.167-1.796-2.14A2.25 2.25 0 00.39 3.5z"></path><path d="M7.5 10.723l.98-1.167.957 1.14a2.25 2.25 0 001.724.804h1.947l-1.017-1.018a.75.75 0 111.06-1.06l2.829 2.828-2.829 2.828a.75.75 0 11-1.06-1.06L13.109 13H11.16a3.75 3.75 0 01-2.873-1.34l-.787-.938z"></path></svg></button>
            <button @click="$emit('backClick')" ref="backBtn"><svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M3.3 1a.7.7 0 01.7.7v5.15l9.95-5.744a.7.7 0 011.05.606v12.575a.7.7 0 01-1.05.607L4 9.149V14.3a.7.7 0 01-.7.7H1.7a.7.7 0 01-.7-.7V1.7a.7.7 0 01.7-.7h1.6z"></path></svg></button>
            <button @click="$emit('playPauseClick', 'teste1')" ref="playPauseBtn">
              <svg v-show="props.loaded == false" role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M3 1.713a.7.7 0 011.05-.607l10.89 6.288a.7.7 0 010 1.212L4.05 14.894A.7.7 0 013 14.288V1.713z"></path></svg>
              <svg v-show="props.loaded == true" role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 eqtHWV"><path d="M2.7 1a.7.7 0 00-.7.7v12.6a.7.7 0 00.7.7h2.6a.7.7 0 00.7-.7V1.7a.7.7 0 00-.7-.7H2.7zm8 0a.7.7 0 00-.7.7v12.6a.7.7 0 00.7.7h2.6a.7.7 0 00.7-.7V1.7a.7.7 0 00-.7-.7h-2.6z"></path></svg>
              </button>
            <button @click="$emit('nextClick')" ref="nextBtn"><svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M12.7 1a.7.7 0 00-.7.7v5.15L2.05 1.107A.7.7 0 001 1.712v12.575a.7.7 0 001.05.607L12 9.149V14.3a.7.7 0 00.7.7h1.6a.7.7 0 00.7-.7V1.7a.7.7 0 00-.7-.7h-1.6z"></path></svg></button>
            <button @click="$emit('repeatClick')" ref="repeatBtn"><svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M0 4.75A3.75 3.75 0 013.75 1h8.5A3.75 3.75 0 0116 4.75v5a3.75 3.75 0 01-3.75 3.75H9.81l1.018 1.018a.75.75 0 11-1.06 1.06L6.939 12.75l2.829-2.828a.75.75 0 111.06 1.06L9.811 12h2.439a2.25 2.25 0 002.25-2.25v-5a2.25 2.25 0 00-2.25-2.25h-8.5A2.25 2.25 0 001.5 4.75v5A2.25 2.25 0 003.75 12H5v1.5H3.75A3.75 3.75 0 010 9.75v-5z"></path></svg></button>
        </div>

        <div class="player-controller-track">
            <div class="player-controller-start-time">
                {{ props.track.trackTime }}
            </div>
            <div class="player-controller-track-trackbar">
                <div id="inside-trackbar">
                    <div id="tracked"></div>
                </div>
            </div>
            <div class="player-controller-end-time">
                6:49
            </div>
        </div>
    </div>
    <div class="player-volume-controller">
        <button class="player-volume-controller-button1">
            <svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M15 15H1v-1.5h14V15zm0-4.5H1V9h14v1.5zm-14-7A2.5 2.5 0 013.5 1h9a2.5 2.5 0 010 5h-9A2.5 2.5 0 011 3.5zm2.5-1a1 1 0 000 2h9a1 1 0 100-2h-9z"></path></svg>
        </button>
        <button class="player-volume-controller-button2">
            <svg role="presentation" height="16" width="16" class="Svg-ytk21e-0 jAKAlG" aria-label="Conectar a um dispositivo" viewBox="0 0 16 16"><path d="M6 2.75C6 1.784 6.784 1 7.75 1h6.5c.966 0 1.75.784 1.75 1.75v10.5A1.75 1.75 0 0114.25 15h-6.5A1.75 1.75 0 016 13.25V2.75zm1.75-.25a.25.25 0 00-.25.25v10.5c0 .138.112.25.25.25h6.5a.25.25 0 00.25-.25V2.75a.25.25 0 00-.25-.25h-6.5zm-6 0a.25.25 0 00-.25.25v6.5c0 .138.112.25.25.25H4V11H1.75A1.75 1.75 0 010 9.25v-6.5C0 1.784.784 1 1.75 1H4v1.5H1.75zM4 15H2v-1.5h2V15z"></path><path d="M13 10a2 2 0 11-4 0 2 2 0 014 0zm-1-5a1 1 0 11-2 0 1 1 0 012 0z"></path></svg>
        </button>
        <button class="player-volume-controller-volumebar">
            <svg role="presentation" height="16" width="16" aria-label="Volume médio" id="volume-icon" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M9.741.85a.75.75 0 01.375.65v13a.75.75 0 01-1.125.65l-6.925-4a3.642 3.642 0 01-1.33-4.967 3.639 3.639 0 011.33-1.332l6.925-4a.75.75 0 01.75 0zm-6.924 5.3a2.139 2.139 0 000 3.7l5.8 3.35V2.8l-5.8 3.35zm8.683 6.087a4.502 4.502 0 000-8.474v1.65a2.999 2.999 0 010 5.175v1.649z"></path></svg>
            <div class="player-volume-controller-volumebar-wrapper">
                <div class="player-volume-controller-volumebar-trackbar">
                    <div class="player-volume-controller-volumebar-tracked">
                        
                    </div>
                </div>
            </div>
        </button>
        <button class="player-volume-controller-button3">
            <svg role="img" height="16" width="16" viewBox="0 0 16 16" class="Svg-ytk21e-0 jAKAlG"><path d="M6.53 9.47a.75.75 0 010 1.06l-2.72 2.72h1.018a.75.75 0 010 1.5H1.25v-3.579a.75.75 0 011.5 0v1.018l2.72-2.72a.75.75 0 011.06 0zm2.94-2.94a.75.75 0 010-1.06l2.72-2.72h-1.018a.75.75 0 110-1.5h3.578v3.579a.75.75 0 01-1.5 0V3.81l-2.72 2.72a.75.75 0 01-1.06 0z"></path></svg>
        </button>
    </div>
  </div>
</template>