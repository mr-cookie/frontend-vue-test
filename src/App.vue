<template>
  <div id="app">
   <validate-component name="c 1" >
      <some-component name="some 1" >
         <validate-component name="c 2" ></validate-component>
      </some-component>
      <some-component name="some 2" >
        <validate-component name="c 3" >
          <validate-component name="c 4">
            <validate-component name=" --c 8" />
            <validate-component name="--c 9" />
          </validate-component>
          <validate-component name="--c 7" />
        </validate-component>
        <validate-component name="--c 6"  />
      </some-component>
      <validate-component name="c 5" ></validate-component>
    </validate-component> 
  </div>
</template>

<script>
import validateComponent from './components/validateComponent.vue'
import someComponent from './components/someComponent.vue'
export default {
  name: 'App',
  components: {
   validateComponent,
   someComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
