<template>
 <div id="app">
    <header>
        <h1>My Music</h1>
    </header>
    <main>
        <section class="player">
            <h2 class="song-title">{{current.title}} - <span>{{current.artist}}</span>
            </h2>
            <div class="control">
              <button class="prev">Prev</button>
              <button class="play" v-if="!isPlaying">Play</button>
              <button class="pause" v-else>Pause</button>
              <button class="next">Next</button>
            </div>
             

        </section>

    </main>
 </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [ 
        {
          title: 'Grateful',
          artist: 'Neffex',
          src: require ('./assets/neffex-grateful.mp3')

        },

        {
          title: 'Invincible',
          artist: 'Deaf Kev',
          src: require ('./assets/deaf-kev-invincible.mp3')
        }
        
      ],
      player: new Audio()
    }
  },
  methods: {
    play (song) {
      if (typeof song.src != "undefined") {
        this.curent = song;
        this.player.src = this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
    }
  },

  
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    //  
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  
}

body {
  font-family: sans-serif;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color: #212121;
  color: #FFF;

}

</style>
