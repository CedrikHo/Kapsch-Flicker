<template>

  <div id="app">
<header class="page-header">
    <h1>Flickr Image Grabber Cedrik
</h1>
</header>

    <main>
     <title> Flickr Image Grabber </title>
    <button @click="fetchPicture">click this for other thing</button>

        <div class="response title">{{ response.title }}</div>
        <img src={{response.media[1]}}>

        <footer>
  <p>Images retrieved using the Flickr Public API
Designed for the Kapsch Interview Process
6/9/2021</p>
</footer>

    </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
   return {
   query: '',
   response: {},
    imglink: '',
    }
  },
  methods:{
   

    fetchPicture (){
        console.log("hit fetch Picture");
        fetch ('http://www.flickr.com/services/feeds/photos_public.gne?tags=puppy&format=json&jsoncallback=?',
          { 
                mode: 'no-cors'  
             } )
  .then(response => response.json())
  .then(data => this.setResults(data));

      
    },

    setResults(results){
      this.response = results;
     
    }
  }
  
}

</script>

<style>
#app {
background-image: url('./assets/Yellow-Desk-Simple-Background-Image.jpg');

background-size: cover;
background-position: bottom;
transition: 0.4s;
}

main {
min-height: 100vh;
padding: 25px;
 background-image: linear-gradient(to bottom, rgba(0,0,0,0.25) ,rgba(0,0,0,0.75) ) ;

}
*{
margin: 0;
padding: 0;
box-sizing: border-box;
}

body{
  font-family: 'montserrat', sans-serif;
}



</style>
