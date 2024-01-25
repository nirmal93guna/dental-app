<template>
    <div class="main-wrapper">
        <slot></slot>
    </div>
</template>
  
<script>
// @ is an alias to /src

export default {
    name: 'MainWrapper',
}
</script>
<style>
.main-wrapper {
    height: calc(100vh - 16px);
    width: calc(100vw - 16px);
    position: relative;
}
</style>
  