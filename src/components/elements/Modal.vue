<template>
<div class="modal" :class="{ 'is-active': active }">
  <div class="modal-background" @click="this.$emit('cancel')"></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">{{ title }}</p>
      <button class="delete" aria-label="close"></button>
    </header>
    <section class="modal-card-body">
      <slot></slot>
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success" @click="this.$emit('success')">{{ primaryLabel }}</button>
      <button class="button" @click="this.$emit('cancel')">Cancel</button>
    </footer>
  </div>
</div>
</template>

<script>
export default {
    name: 'Modal',
    props: {
        title: String,
        primaryLabel: String,
        active: Boolean
    }
}
</script>

<style>
.modal .modal-card-body {
    color: black;
    font-size: 18px;
    

}
</style>