<template>
    <main class="container mt-3">
        <h1>Add Contact</h1>
        <section class="row">
            <article class="col-md-6">
                <FormControl v-bind:name="name" v-on:changeName="name = $event" v-bind:image="image"
                    v-on:changeImage="image = $event" v-bind:email="email" v-on:changeEmail="email = $event"
                    v-bind:contact="contact" v-on:changeContact="contact = $event" />
                <div class="form-group">
                    <button class="btn btn-success pl-4 pr-4">Create</button>
                </div>
            </article>
            <article class="col-md-6">

            </article>
        </section>
    </main>
</template>

<script>
import FormControl from '../../components/FormControl.vue';
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
    }
}
</script>