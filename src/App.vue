<template>
  <div class="wrapper">
    <div class="wrapper-content">
      <section>
        <div class="container">
          <button class="btn" @click="modalFirst = !modalFirst">Show first modal</button>

          <!-- first modal -->
          <modal
              title="First modal"
              v-show="modalFirst"
              @close="modalFirst = false">
            <!-- body -->
            <div slot="body">
              <p> That slot works </p>
              <button class="btn" @click="modalFirst = false">Close modal!</button>
            </div>
          </modal>

          <!-- second modal -->
          <button class="btn" @click="modalSecond.show = !modalSecond.show">Show second modal</button>
          <modal
              title="Modal with form"
              v-show="modalSecond.show"
              @close="modalSecond.show = false">
            <!-- body -->
            <div slot="body">
              <form @submit.prevent="submitSecondForm">
                <label>Name:</label>
                <input type="text" required v-model="modalSecond.name">
                <label>E-mail:</label>
                <input type="email" required v-model="modalSecond.email">
                <button class="btn">Submit</button>
              </form>
            </div>
          </modal>
            <!-- Modal with validate-->
              <button class="btn" @click="modalValidate = !modalValidate">Modal validate</button>
              <modalValidate v-show="modalValidate" @close="modalValidate = false"/>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import modal from '@/components/UI/Modal.vue'
import modalValidate from '@/components/ModalValidate.vue'

export default {
  components: {modal, modalValidate},
  data() {
    return {
      modalFirst: false,
      modalValidate: false,
      modalSecond: {
        show: false,
        name: '',
        email: ''
      }
    }
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = '';
          this.modalSecond.email = '';
          this.modalSecond.show = false;
    }
  }
}

</script>
<style lang="scss">
.btn {
  padding: 15px;
  background-color: coral;
  border-radius: 8px;
  cursor: pointer;
  font-family: inherit;
}
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  input {
    height: auto;
    border-radius: 6px;
    padding: 10px;
    margin: 10px;
    min-width: 400px;
  }
}

</style>
