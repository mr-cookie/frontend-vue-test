<template>
  <div style="border:1px dotted red; padding: 5px; margin:5px">
  some {{name}}
  <slot></slot>

  </div>
  
</template>
<script>
export default{
  name: 'someComponent',
  props:['name'],
}
</script>
