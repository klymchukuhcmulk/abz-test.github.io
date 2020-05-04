<template>
    <div class="registration">
        <div class="reg-wrap">
            <header>
                <h1>Register to get a work</h1>
                <p>Attention! After successful registration and alert, update the list of users in the block from the top</p>
            </header>
            <form>
                <div :class="{nameError : nameError}">
                    <label for="name"><p class="label-p">Name</p></label>
                    <input @focus="focused.name = true"  v-model="name" type="text" id="name" placeholder="Your name">
                    <span>Error</span>
                </div>

                <div :class="{phoneError : emailError}">
                    <label for="name"><p class="label-p">Email</p></label>
                    <input @focus="focused.email = true" v-model="email" type="text" id="email" placeholder="Your email">
                    <span>Error</span>
                </div>

                <div :class="{phoneError : phoneError}">
                    <label for="name"><p class="label-p">Phone number</p></label>
                    <input @focus="focused.phone = true" v-model="phone" type="text" id="phone" placeholder="+380 XX XXX XX XX">
                    <span>Error</span>
                </div>
                <p class="radio-title">Select your position</p>
                <p class="radio-p"><input v-model="workPosition" type="radio" name="position" id="frontend" value="Frontend developer"><label for="name">Frontend developer</label></p>
                <p class="radio-p"><input v-model="workPosition" type="radio" name="position" id="backend" value="Backend developer"><label for="name">Backend developer</label></p>
                <p class="radio-p"><input v-model="workPosition" type="radio" name="position" id="designer" value="Designer"><label for="name">Designer</label></p>
                <p class="radio-p"><input v-model="workPosition" type="radio" name="position" id="qa" value="QA"><label for="name">QA</label></p>
                <p class="radio-p">Photo</p>
                <div class="photo-input">Upload your photo <div class="photo-before">Browse</div></div>
                <button :disabled="error" class="singleBtn" @click="submitForm"><p>Sign up now</p></button>
            </form>
        </div>
        <modal-window v-if="modalOn" @close="modalOn = false"/>
    </div>
</template>

<script>
    import ModalWindow from './ModalWindow'
    export default {
      name: "Registration",
      data () {
        return {
          name: '',
          email: '',
          phone: '',
          modalOn: false,
          workPosition: '',
          focused: {
            name: false,
            phone: false,
            email: false
          }
        }
      },
      components: {
        ModalWindow
      },
      methods: {
        submitForm () {
          console.log('submit')
          this.$emit('add', {
            name: this.name,
            email: this.email,
            phone: this.phone,
            workPosition: this.workPosition,
            img: require('@/assets/photo-cover.svg')
          })
          this.modalOn = true
          this.name = this.phone = this.email = this.workPosition = ''
          this.focused.email = this.focused.phone = this.focused.name = false
        }
      },
      computed: {
        error () {
          if (!this.nameError && !this.emailError && !this.phoneError && !this.workError) {
            return false
          }
          return true
        },
        workError () {
          if (this.workPosition === '') {
            return true
          }
          return false
        },
        nameError () {
          if (this.focused.name && this.name.trim().length === 0) {
            return  true
          }
          return false
        },
        emailError () {
          // eslint-disable-next-line no-useless-escape
          const emailReg = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/g
          if (this.focused.email && !emailReg.test(this.email)) {
            return true
          }
          return false
        },
        phoneError () {
          // eslint-disable-next-line no-useless-escape
          const phoneReg = /^[+]*[3]{1}[8]{1}[0]{1}\s[0-9]{2}\s[0-9]{3}\s[0-9]{2}\s[0-9]{2}$/g
          if (this.focused.phone && !phoneReg.test(this.phone)) {
            return true
          }
          return false
        }
      }
    }
</script>

<style scoped>

</style>
