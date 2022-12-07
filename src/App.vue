<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <button class="btn" @click="modalFirst = !modalFirst">Show first modal</button>
          <!-- first modal -->
          <modals
              title="First modal"
              v-show="modalFirst"
              @close="modalFirst = !modalFirst">
            <!-- body -->
            <div slot="body">
              <p> That slot works </p>
              <button class="btn" @click="modalFirst = !modalFirst">Close modal!</button>
            </div>
          </modals>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import modals from '@/components/Modal.vue'
export default {
  components: { modals },
  data () {
    return {
      modalFirst: false
    }
  }
}
</script>
<style lang="scss" scoped>
.btn {
  padding: 15px;
  background-color: coral;
  border-radius: 8px;
  cursor: pointer;
  font-family: inherit;
}

</style>
