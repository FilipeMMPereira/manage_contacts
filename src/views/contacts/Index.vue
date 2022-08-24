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


        <section class="row">
            <article class="col-md-6">
                <div class="card my-2 list-group-item-cussess shadow-lg">
                    <div class="card-body">
                        <section class="row align-items-center justify-content-between">
                            <article class="col-sm-4">
                                <img src="https://th.bing.com/th/id/OIP.fqSvfYQB0rQ-6EG_oqvonQHaHa?pid=ImgDet&rs=1"
                                    alt="" class="contact-image">
                            </article>
                            <article class="col-sm-7">
                                <ul class="list-group">
                                    <li class="list-group-item">Name: <span class="fw-bold">Name</span></li>
                                    <li class="list-group-item">Email: <span class="fw-bold">Email</span></li>
                                    <li class="list-group-item">Contact: <span class="fw-bold">Contact</span></li>
                                </ul>
                            </article>
                            <article class="col-sm-1  d-flex flex-column justify-content-center align-items-center">
                                <router-link to="/details/:id" class="btn btn-md btn-warning my-1"><i class="fa fa-eye"></i></router-link>
                                <router-link to="/details/:id" class="btn btn-primary my-1"><i class="fa fa-edit"></i></router-link>
                                <router-link to="/details/:id" class="btn btn-danger my-1"><i class="fa fa-trash"></i></router-link>
                            </article>
                        </section>
                    </div>
                </div>
            </article>
        </section>


    </main>
</template>