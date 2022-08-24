<template>
    <main class="container mt-3">
        <h1>Add Contact</h1>
        <form v-on:submit.prevent="addContact()">
            <section class="row">
            <article class="col-md-6">
                <FormControl 
                v-bind:name="name" v-on:changeName="name = $event" 
                v-bind:image="image" v-on:changeImage="image = $event" 
                v-bind:email="email" v-on:changeEmail="email = $event"
                v-bind:contact="contact" v-on:changeContact="contact = $event" 
                    />
                <div class="form-group">
                    <button class="btn btn-success pl-4 pr-4">Create</button>
                </div>
            </article>
            <article class="col-md-4">
                <img v-bind:src="image" alt="" class="contact-image-large">
            </article>
        </section>
        </form>
    </main>
</template>

<script>
import FormControl from '../../components/FormControl.vue';
import { ContactService } from '../../services/contact';
export default {
    components: {
        FormControl
    },
    data() {
        return {
            name: '',
            image: '',
            email: '',
            contact: '',
        }
    },
    methods: {
        addContact: async function () {
            try {
                let contact = {
                    name: this.name,
                    image: this.image,
                    email: this.email,
                    contact: this.contact,
                }
                let response = await ContactService.createContact(contact)
                if(response){
                    return this.$router.push('/')
                }else{
                    return this.$router.push('/add')
                }
            } catch (error) {
                console.log(error)
            }
        }
    }
}
</script>