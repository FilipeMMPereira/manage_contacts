<template>
    <main class="container mt-3">
        <section class="row align-items-center">
            <article class="col-md-6">
                <h1>Contact Manager</h1>
            </article>
            <article class="col-md-6 text-right">
                <router-link to="/add" class="btn btn-success">+ New</router-link>
            </article>
        </section>

        <!-- <pre>{{contacts}}</pre> -->
        <section class="row mt-5" v-if="contacts.length > 0">
            <article class="col-md-6" v-for="contact in contacts" v-bind:key="contact">
                <div class="card my-2 list-group-item-cussess shadow-lg">
                    <div class="card-body">
                        <section class="row align-items-center justify-content-between">
                            <article class="col-sm-4">
                                <img v-bind:src="contact.image" alt="" class="contact-image">
                            </article>
                            <article class="col-sm-7">
                                <ul class="list-group">
                                    <li class="list-group-item">Name: <span class="fw-bold">{{ contact.name }}</span>
                                    </li>
                                    <li class="list-group-item">Email: <span class="fw-bold">{{ contact.email }}</span>
                                    </li>
                                    <li class="list-group-item">Contact: <span class="fw-bold">{{ contact.contact
                                    }}</span></li>
                                </ul>
                            </article>
                            <article class="col-sm-1  d-flex flex-column justify-content-center align-items-center">
                                <router-link v-bind:to="`/details/${contact.id}`" class="btn btn-md btn-warning my-1"><i
                                        class="fa fa-eye"></i></router-link>
                                <router-link v-bind:to="`/edit/${contact.id}`" class="btn btn-primary my-1"><i
                                        class="fa fa-edit"></i></router-link>
                                <button class="btn btn-danger my-1" v-on:click="deleteContact(contact.id)" id="myBtn"><i
                                        class="fa fa-trash"></i></button>
                            </article>
                        </section>
                    </div>
                </div>
            </article>
        </section>


        <!-- modal that allows you to delete record -->
        <div id="myModal" class="modal">

            <!-- Modal content -->
            <div class="modal-content">
                <div class="text-right">
                    <span class="close">&times;</span>

                </div>
                <p>Are you sure you want to delete?</p>

                <button class="btn btn-success mb-3" v-on:click.prevent="confirm()">Confirm</button>
                <button class="btn btn-secondary" v-on:click.prevent="cancel()">Cancel</button>
            </div>

        </div>

    </main>
</template>

<script>
import { ContactService } from '../../services/contact'
// import $ from 'jquery'
export default {
    data() {
        return {
            contacts: [],
            contactDeleteID: ''
        }
    },
    created: async function () {
        try {
            let response = await ContactService.getAllContacts()
            this.contacts = response.data
        } catch (error) {
            console.log(error)
        }
    },
    methods: {
        deleteContact: async function (id) {
            console.log(id)
            this.contactDeleteID = id
            // try {
            //     let response = await ContactService.deleteContact(id)
            //     if (response) {
            //         let response = await ContactService.getAllContacts()
            //         this.contacts = response.data
            //     }
            // } catch (error) { console.log(error) }
            // $("#exampleModal").modal("show");
            var modal = document.getElementById("myModal");
            modal.style.display = "block";
        },
        confirm: async function () {
            // console.log(id)
            // this.contactDeleteID = id
            try {
                let response = await ContactService.deleteContact(this.contactDeleteID)
                if (response) {
                    let response = await ContactService.getAllContacts()
                    this.contacts = response.data
                    var modal = document.getElementById("myModal");
                    modal.style.display = "none";
                }
            } catch (error) { console.log(error) }
        },
        cancel() {
            var modal = document.getElementById("myModal");
            modal.style.display = "none";
        }
    }

}

</script>