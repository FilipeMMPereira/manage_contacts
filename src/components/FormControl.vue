<template>
    <section>
        <div class="form-group">
            <input type="text" class="form-control" placeholder="Name" v-bind:value="name" v-on:input="$emit('changeName',$event.target.value)">
        </div>
        <div class="form-group">
            <input type="text" class="form-control" placeholder="Image URL" v-bind:value="image" v-on:input="$emit('changeImage',$event.target.value)">
        </div>
        <div class="form-group">
            <input type="text" class="form-control" placeholder="Email" v-bind:value="email" v-on:input="$emit('changeEmail',$event.target.value)">
        </div>
        <div class="form-group">
            <input type="number" class="form-control" placeholder="Contact" v-bind:value="contact" v-on:input="$emit('changeContact',$event.target.value)">
        </div>
        
    </section>
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            default: ''
        },
        image: {
            type: String,
            default: ''
        },
        email: {
            type: String,
            default: ''
        },
        contact: {
            type:Number,
        },

    },

}
</script>