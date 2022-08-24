<template>
    <main class="container mt-3">
        <h1>Details</h1>
        <section class="row mt-5 align-items-center">
            <article class="col-md-4">
                <img v-bind:src="contact.image" alt=""
                    class="contact-image-large">
            </article>
            <article class="col-md-6">

                <ul class="list-group">
                    <li class="list-group-item">Id: <span class="fw-bold">{{contact.id}}</span></li>
                    <li class="list-group-item">Name: <span class="fw-bold">{{contact.name}}</span></li>
                    <!-- <li class="list-group-item">Image URL: <span class="fw-bold">https://th.bing.com/th/id/OIP.fqSvfYQB0rQ-6EG_oqvonQHaHa?pid=ImgDet&rs=1</span></li> -->
                    <li class="list-group-item">Email: <span class="fw-bold">{{contact.email}}</span></li>
                    <li class="list-group-item">Contact: <span class="fw-bold">{{contact.contact}}</span></li>

                </ul>
            </article>
            <article class="col-md-12">
                <router-link to="/" class="btn btn-success mt-5">Back</router-link>
            </article>
        </section>

    </main>
</template>


<script>
import { ContactService } from '../../services/contact'
export default{
    data:function(){
        return{
            contactId:this.$route.params.id,
            contact:{}
        }
    },
    created:async function(){
        try{
            let response=await ContactService.getContact(this.contactId)
            this.contact=response.data
        }catch(error){
            console.log(error)

        }
    },
}
</script>