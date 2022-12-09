<template>
    <h1>Job Details Page</h1>
    <p>The Job ID is: {{ id }}</p>
</template>


<script>
export default {
    // ---props müssen in der speziefischen route im index.js freigegeben ("props: true") werden.
    props: ["id"]
    // ---Alternative zu props-Variante---
    // data() {
    //     return {
    //         id: this.$route.params.id
    //     }
    // }
}

</script>