<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{$store.state.message}}</p>
    <hr>
    <pre>[{{now}}]</pre>
    <div class="link"
    @click="$store.commit('doit')">
        <a @click.stop="$store.commit('reset')">
          clicked: {{ $store.state.counter }}
        </a>
    </div>
    <router-link to="/other">Go to Other</router-link>
  </section>
</template>

<script>
export default {
  data: function () {
    return {
      title:'Index',
      message:'this is root page.',
      now: 'wait'
    }
  },
  methods: {
    doAction: function(){
      this.$store.state.counter++;
    }
  },
  created: function () {
   setInterval(() => {
     var d =new Date();
     this.now =d.getHours()
     + ':'+ d.getMinutes()
     + ':'+ d.getSeconds()
   }, 1000);
  }
}
</script>

<style>
.container {
  padding: 5px 10px;
}

h1{
  font-size: 60pt;
  color: #345980;
}
p{
  padding-top: 5px;
  font-size: 20pt;
}
pre{
  padding: 10px;
  font-size: 18pt;
  background-color: #efefef;
}
hr{
  margin: 10px 0px;
}

</style>
