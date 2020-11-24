<template>
    <div>
        <h1>{{ num }}{{name}}</h1>
        <small>{{url}}</small>
    </div>
</template>

<script>
export default {
    props: {
        num: Number,
        name: String,
        url: String
    }
}

</script>

<style lang="stylus">

</style>