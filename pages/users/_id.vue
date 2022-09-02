<template>
    <section>
        <h1>
            {{$route.params.id}}
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
    }
}
</script>