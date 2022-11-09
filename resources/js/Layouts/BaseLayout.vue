
<template>
  <div class="guify">
    <SideBarLayout></SideBarLayout>
    <section>
      <HeaderLayout></HeaderLayout>
      <div class="music-section" ref="music-section">
        <slot :playSong="(file) => playSong(file)" />
      </div>
    </section>
    <PlayerLayout
      v-show="song"
      :song="song"
      :loaded="componentData.loaded"
      :track="componentData.track"
      @playPauseClick="(file) => playPauseClick(file)"
      @suffleClick="suffleClick()"
      @backClick="backClick()"
      @nextClick="nextClick()"
      @repeatClick="repeatClick()"
    ></PlayerLayout>
    <div id="slotPlayer"></div>
  </div>
</template>

<script setup>
import SideBarLayout from "@/Layouts/SideBarLayout.vue";
import HeaderLayout from "@/Layouts/HeaderLayout.vue";
import PlayerLayout from "@/Layouts/PlayerLayout.vue";
import { Link } from "@inertiajs/inertia-vue3";
import { ref, reactive, onMounted, watch } from "vue";

const list = [
  {
    title: "Rockeira",
    file: "music1.mp3",
    image: "nyan-cat-1.gif",
    actor: "Grupo do ROCK Mané",
  },
  {
    title: "Eletroniqueira",
    file: "music2.mp3",
    image: "cz-logo.webp",
    actor: "Tuts tuts quero ver",
  },
];

const componentData = reactive({
  loaded: false,
  track: {
    trackTime: '0:00',
    trackBar: 0,
  }
});

var slotPlayer = undefined;
var audioplayer = undefined;
var endTime = undefined;
const song = ref(undefined);

function playSong(file) {
  song.value = null;
  setTimeout(() => {
  song.value = list.find((l) => l.file == file);
  slotPlayer = document.getElementById("slotPlayer");
  slotPlayer.innerHTML =
    `<audio controls="" id="audioplayer">
        <source src="musics/` +
    file +
    `" type="audio/mp3" />
      </audio>`;
  audioplayer = document.getElementById("audioplayer");
  componentData.loaded = true;
  audioplayer.play();
  endTime = document.getElementsByClassName("player-controller-end-time")[0];
  },100);

  setTimeout(() => {
    var hours = parseInt(audioplayer.duration / 3600);
    var minutes = parseInt(audioplayer.duration / 60);
    var seconds = parseInt(audioplayer.duration);
    endTime.innerHTML = hours + ":" + minutes + seconds;
  }, 300);
}

function playPauseClick(file) {
  if (componentData.loaded == false) {
    componentData.loaded = true;
    audioplayer.play();
  } else {
    componentData.loaded = false;
    audioplayer.pause();
  }
}

function suffleClick() {
  console.log("suffled playlist");
}

function backClick() {
  console.log("back song");
}

function nextClick() {
  console.log("next song");
}

function repeatClick() {
  console.log("repeat song");
}

watch(song, () => {
  var intervalId = window.setInterval(function () {
    // call your function here
    componentData.track.trackTime = '0:0' + parseInt(audioplayer.currentTime);
    componentData.track.trackBar = (audioplayer.currentTime * 100) / audioplayer.duration;
    if (audioplayer.currentTime == audioplayer.duration)
    {
      clearInterval(intervalId);
    }
  }, 1000);
});

onMounted(() => {
  // console.log(audioplayer.value.innerHTML)
  // console.log(document.querySelectorAll('.test'));
});
</script>