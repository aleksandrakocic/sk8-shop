<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Example Component</div>

                    <div class="card-body" v-for='product in products' :key='product.id'>
                        <p> {{ product.title }} </p>
                        <p> {{ product.description }} </p>
                        <p> {{ product.price }} </p>
                        <p> {{ product.image }} </p>
                        <p> {{ product.category }} </p>
                        
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {

        data() {
            return {
                'products' : []
            }

        },
        mounted() {
            console.log('Component mounted.')
            this.fetchProducts() 
        },
        methods: {
            fetchProducts() {
                axios.get('/api/products')
                    .then(response => {
                        this.products = response.data;
                        console.log(this.products);
                    })
                    .catch((err) => {
                        console.log(err)
                    })
            },
        
        }

    }
</script>