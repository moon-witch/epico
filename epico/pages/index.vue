<script setup lang="ts">
const overlayClosed = ref(false)
const videoPlaying = ref(false)

const onClose = () => {
  overlayClosed.value = true
}
let player: any = null

const revealOne = ref(false)
const setRevealOne = () => {
  revealOne.value = true;
}

const revealTwo = ref(false)
const setRevealTwo = () => {
  revealTwo.value = true;
}

const revealThree = ref(false)
const setRevealThree = () => {
  revealThree.value = true;
}

const revealFour = ref(false)
const setRevealFour = () => {
  revealFour.value = true;
}

const revealFive = ref(false)
const setRevealFive = () => {
  revealFive.value = true
}

watch(overlayClosed, () => {
  if (overlayClosed.value) {
    videoPlaying.value = true
    player.playVideo()

    setTimeout(() => {
      setRevealOne()
    }, 3000)

    setTimeout(() => {
      setRevealTwo()
    }, 6000)

    setTimeout(() => {
      setRevealThree()
    }, 9000)

    setTimeout(() => {
      setRevealFour()
    }, 12000)

    setTimeout(() => {
      setRevealFive()
    }, 15000)
  }
})

const pauseVideo = () => {
  videoPlaying.value = false
  player.pauseVideo()
}

const playVideo = () => {
  videoPlaying.value = true
  player.playVideo()
}

onMounted(() => {
  // Load YouTube IFrame API script
  const tag = document.createElement('script')
  tag.src = 'https://www.youtube.com/iframe_api'
  const firstScriptTag = document.getElementsByTagName('script')[0]
  firstScriptTag.parentNode.insertBefore(tag, firstScriptTag)

  // Define onYouTubeIframeAPIReady function, called by the YouTube API
  window.onYouTubeIframeAPIReady = () => {
    player = new YT.Player('player', {
      height: '950',
      width: '100%',
      videoId: 'YMKIxxRA270',
      playerVars: {
        controls: 0,
        loop: 1
      }
    })
  }
})
</script>

<template>
  <div class="container">
    <Overlay @closed="onClose"/>
    <div id="player"></div>
    <div class="overlay"></div>
    <h1>EPICO, HAPPY BIRTHDAY!!</h1>
    <h2 class="date">04.09.2024</h2>
    <h2 class="one" :class="{'reveal': revealOne}">U are an amazing strimmer & (most importantly) person</h2>
    <h2 class="two" :class="{'reveal': revealTwo}">Thank you for your kind heart for all of us!</h2>
    <h2 class="three" :class="{'reveal': revealThree}">Never forget all the good in the world... because you are part of it!</h2>
    <h2 class="four" :class="{'reveal': revealFour}">Cheers, to all the good stuff that's gonna come your way in the next year!</h2>
    <h2 class="five" :class="{'reveal': revealFive}">Stay humble, stay epic ♡</h2>
    <div  class="video-buttons">
      <button v-if="videoPlaying" @click="pauseVideo" class="video-button">Turn this fkn "music" off!</button>
      <button v-if="!videoPlaying" @click="playVideo" class="video-button">Gimme back da vibes!</button>
    </div>
    <div class="images">
      <a href="https://www.twitch.tv/epic_mystic/clip/RelentlessAggressiveLapwingKappaClaus-Xvxmi5zQAxmlyz2p" target="_blank">
        <img src="../public/epicface.png"  alt="face" class="image face" />
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/MoistAmazonianPuddingDendiFace-dIj9LLjBlj1dE-ke?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/epictag.png"  alt="face" class="image tag"/>
      </a>
      <a href="https://www.twitch.tv/videos/2159075456" target="_blank">
        <img src="../public/epicFollowers.png"  alt="face" class="image followers"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/SplendidSmoggySnailRickroll-B6kWP_AX4d00teJ7?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/facepalm.png"  alt="face" class="image facepalm"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/DiligentEasyStarSoonerLater-BuzK08oRzW4ST21u?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/glasses.png"  alt="face" class="image glasses"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/CuteGoldenMageLitFam-CrqtuvUSaj65Gh7m?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/heart.png"  alt="face" class="image heart"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/ObservantBlitheSlothGingerPower-R5sH9WpKvEfe0-Ov?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/piderman.png"  alt="face" class="image piderman"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/CourageousDifficultWolfSoBayed-okWQBVb-GahQd7ko?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/pray.png"  alt="face" class="image pray"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/BreakableRefinedKeyboardCoolStoryBob-oEFeBH3Qsrjn69Fm?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/shrug.png"  alt="face" class="image shrug"/>
      </a>
      <a href="https://www.twitch.tv/epic_mystic/clip/ProtectiveIgnorantKathyPogChamp-nXkmquAxMAtvbxIs?filter=clips&range=all&sort=time" target="_blank">
        <img src="../public/what.png"  alt="face" class="image what"/>
      </a>
    </div>
    <div class="moontag">♡ made with idiocy by moonwitch ♡</div>
    <div class="click-them">Try clicking things!!!</div>
  </div>
</template>

<style scoped>
h1 {
  color: #bb8ce7;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 4rem;
  animation: jump .3s infinite ease-in-out;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: black;
  opacity: .5;
}

.video-buttons {
  position: absolute;
  bottom: 1%;
  right: 2%;
}

.video-button {
  background: black;
  color: linen;
  border: none;
  border-radius: 5px;
  font-family: "Indie Flower", cursive;
  font-size: 1.5rem;
  z-index: 1000;
}

.images {
  position: absolute;
  top: 0;
  left: 0;
  height: 90dvh;
  width: 100%;
}

.image {
  border-radius: 50px;
}

.face {
  border-radius: 50px;
  position: absolute;
  top: 0;
  rotate: -10deg;
}

.tag {
  position: absolute;
  top: 1%;
  left: 20%;
  border-radius: 10px;
}

.followers {
  position: absolute;
  top: 1%;
  right: 1%;
  border-radius: 10px;
}

.facepalm {
  position: absolute;
  top: 60%;
  left: 2%;
  animation: wiggle 2s infinite ease-in-out;
}

.glasses {
  position: absolute;
  top: 10%;
  right: 2%;
  animation: wiggle 2.5s infinite ease-in-out;
}

.heart {
  position: absolute;
  top: 15%;
  right: 45%;
  animation: wiggle .4s infinite ease-in-out;
}

.piderman {
  position: absolute;
  top: 70%;
  right: 10%;
  animation: wiggle 3s infinite ease-in-out;
}

.pray {
  position: absolute;
  top: 30%;
  right: 20%;
  animation: wiggle 1.5s infinite ease-in-out;
}

.shrug {
  position: absolute;
  top: 80%;
  right: 80%;
  animation: wiggle 1s infinite ease-in-out;
}

.what {
  position: absolute;
  top: 90%;
  right: 45%;
  animation: weirdMove 20s infinite ease-in-out;
}

.date {
  color: #bb8ce7;
  position: absolute;
  top: 55%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 4rem;
  animation: jump .3s infinite ease-in-out;
}

.one {
  position: absolute;
  top: 5%;
  left: 30%;
  rotate: -5deg;
  opacity: 0;
}

.two {
  position: absolute;
  top: 17%;
  left: 70%;
  rotate: 10deg;
  opacity: 0;
}

.three {
  position: absolute;
  top: 39%;
  left: 70%;
  rotate: -10deg;
  opacity: 0;
}

.four {
  position: absolute;
  top: 45%;
  left: 10%;
  rotate: -15deg;
  opacity: 0;
}

.five {
  position: absolute;
  top: 70%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
}

.reveal {
  animation: reveal .5s forwards ease-in-out;
}

.click-them {
  position: absolute;
  top: .5%;
  left: 50%;
  transform: translateX(-50%);
  font-weight: bold;
}

.moontag {
  font-weight: bold;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}

@keyframes jump {
  0%, 100% {
    transform: translateX(-50%) translateY(-50%);
  }
  50% {
    transform: translateX(-50%) translateY(-20px);
  }
}

@keyframes wiggle {
  0%, 100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(-5deg);
  }
  50% {
    transform: rotate(5deg);
  }
  75% {
    transform: rotate(-5deg);
  }
}

@keyframes weirdMove {
  0% {
    transform: translate(0, 0);
  }
  10% {
    transform: translate(30px, -20px);
  }
  20% {
    transform: translate(-50px, 30px);
  }
  30% {
    transform: translate(80px, -50px);
  }
  40% {
    transform: translate(-70px, 70px);
  }
  50% {
    transform: translate(50px, 100px);
  }
  60% {
    transform: translate(-100px, -100px);
  }
  70% {
    transform: translate(120px, 50px);
  }
  80% {
    transform: translate(-80px, 120px);
  }
  90% {
    transform: translate(100px, -50px);
  }
  100% {
    transform: translate(0, 0);
  }
}

@keyframes reveal {
  from {
    opacity: 0;
  } to {
  opacity: 1;
      }
}
</style>