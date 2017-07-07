<template>
  <div>
    <p>{{id}}</p>
  </div>
</template>

<script>
import peerjs from 'peerjs/dist/peer.js';

export default {
  name: 'hello',
  data () {
    return {
      peer: null,
      id: null,
    }
  },
  created () {
    this.peer = new Peer({key: 'lwjd5qra8257b9'});
    this.peer.on('open', function(id) {
      this.id = id;
      console.log('My peer ID is: ' + id);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
