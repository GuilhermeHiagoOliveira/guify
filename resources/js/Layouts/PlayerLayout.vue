<script setup>
import { ref, onMounted } from "vue";


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

</script>

<template>
  <div class="player-bar">
    <div class="player-actual-music">
      <div class="player-actual-music-image">
        <img src="img/nyan-cat-1.gif" alt="" />
      </div>
      <div class="player-actual-music-infos">
        <div class="player-actual-music-title">
          <div>
            <label
              id="player-label-music-title"
              @mouseover="changeStatus('standing')"
              @mouseleave="changeStatus('leaved')"
              >testandooooooooooooooooooooooooo0/1111</label
            >
          </div>
        </div>
        <div class="player-actual-music-singer">
          <label>Grupo Alcaxofra com Mel</label>
        </div>
      </div>
    </div>
    <div class="player-controller">a</div>
    <div class="player-volume-controller">a</div>
  </div>
</template>