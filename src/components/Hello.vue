<template>
  <div>
    <p>{{id}}</p>

    <input type="text" v-model="idToConnect"/>
    <button @click="connect">Connect</button>
  </div>
</template>

<script>
import peerjs from 'peerjs/dist/peer.js';

export default {
  name: 'hello',
  data () {
    return {
      peer: null,
      id: '',
      idToConnect: '',
    }
  },
  methods: {
    connect: function(){
      var conn = this.peer.connect(this.idToConnect);
      conn.on('open', function(){
        conn.send('hi!');
      });
    }
  },
  created () {
    this.peer = new Peer({key: 'lwjd5qra8257b9'});
    this.peer.on('open', function(id) {
      this.id = id;
      console.log('My peer ID is: ' + id);
    });

    this.peer.on('connection', function(conn) {
      console.log("Connection works");
      
      conn.on('data', function(data) {
        console.log('Received', data);
      });
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
