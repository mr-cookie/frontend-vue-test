<template>
  <div style="border: 1px solid blue; padding: 5px; margin: 5px">
    <span :style="styleOfName">{{name}}</span>
    <Button @click="runMethod('validate')"> run validate</Button>
    <Button @click="runMethod('reset')"> reset </Button>
  <slot></slot>
  </div>
  
</template>

<script>
export default{
  name: 'validateComponent',
  data(){
    return {
      styleOfName: '',
    }
  },
  props:[
    'name'
  ],
   
  methods: {
    validate(){
      console.log('up :' + this.name)
      this.styleOfName="font-weight:bold;color:red";
    },

    reset(){
      this.styleOfName = '';
      console.log('down :' + this.name)
    },

    runMethod(methodName){
      console.log('--- begin ' + methodName + ' call from ' + this.name);
      for(let i=0; i < this.$children.length; i++){
        if (this.$children[i][methodName]){
           this.$children[i][methodName]() 
        } else {
         this.findAndRunMethod(this.$children[i], methodName) 
        }
      }
      console.log('----- end ' + methodName + ' call from ' + this.name); 
    },

    findAndRunMethod(elem, method){
        for(let i=0; i < elem.$children.length; i++){
          if (!elem.$children[i][method]){
             this.findAndRunMethod(elem.$children[i], method);
          } else {
              elem.$children[i][method]()
            }  
        }
    },
  },
}

</script>
