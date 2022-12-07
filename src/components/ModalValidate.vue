<template>
  <modal
      title="Modal with form and validate"
      @close="$emit('close')">
    <!-- body -->
    <div slot="body">
      <form @submit.prevent>
        <label>Name:</label>
        <input type="text" required >
        <label>E-mail:</label>
        <input type="email" required >
        <button class="btn" >Submit</button>
      </form>

    </div>
  </modal>
</template>

<script>
import modal from '@/components/UI/Modal.vue'
export default {
  components: {modal}
}
</script>