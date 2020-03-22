<template>
  <div>
    <h3>{{item.name}}</h3>
    <p>{{item.link}}</p>
  </div>
</template>
<script>
export default {
  props: ['item']
}
</script>
