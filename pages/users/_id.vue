<template>
    <section>
        <h1>
            {{user.name}}
            <hr>
            {{user.email}}
        </h1>
    </section>
</template>
<script>
export default {
    // props: {
    //     id: {
    //         type: Number,
    //         default: 1
    //     } 
    // },
    validate({params}){
        console.log('validate')
        return /^\d+$/.test(params.id)
    },

    

    async asyncData({$axios, params}){
        const user = await $axios.$get(`https://jsonplaceholder.typicode.com/users/` + params.id)
        return {user}
    }
}
</script>