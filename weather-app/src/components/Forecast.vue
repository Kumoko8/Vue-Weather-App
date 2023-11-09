<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <section>
        <h2>Current Weather</h2>
            <section id="current-weather">

            </section>
    </section>
    <section>
        <h2>5 Day Forecast</h2>
            <section id="five-day">
                <!-- <div>
                    <div>Date</div>
                    <div>temp</div>
                    <div>wind</div>
                </div> -->
            </section>
    </section>
   <section class="search">
    <input id="city-input" type="text" placeholder="Type city name"> 
    <button id="search-btn" type="submit">Search</button>
   </section>

   <h4> Search History</h4>
   <section id="hist"> 

   </section>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
