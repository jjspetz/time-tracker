<template>
  <div class="panel panel-default">
    <div class="panel-heading">
      <h2 class="text-center">Total Time</h2>
    </div>

    <div class="panel-body">
      <h2 class="text-center">{{ time }} hours</h2>
    </div>

  </div>
</template>

<script>
  export default {
    props: ['time']
  }
</script>
