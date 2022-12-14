<template>
    <!-- v-if="job" stellt sicher, dass die Seite erst angezeigt wird, wenn das "job" Data-Objekt einen Wert hat.
    --- null = falsy Value/false (es wird also nicht angezeigt) / Wert = true
    Der Wert wird aus dem fetch geholt, da "job" aber vor dem fetch noch "null" ist, würde ohne die v-if-
    Sicherung ein Error entstehen.
 -->
    <div v-if="job">
        <h1>Job Details Page</h1>
        <h2>{{ job.title }}</h2>
        <h3>{{ job.details }}</h3>
        <p>The Job ID is: {{ id }}</p>
    </div>
    <!-- v-else hier optionale Anzeige, während das "job"-Data-Objekt vom fetch gefüllt wird-->
    <div v-else>Loading jobs...</div>
</template>


<script>
export default {
    props: ["id"],
    data() {
        return {
            job: null
        }
    },
    mounted() {
        fetch("http://localhost:3000/jobs/" + this.id)
        .then(res => res.json())
        .then(content => this.job = content)
        .catch(err => console.log(err.message))
    }




    //VERSION 1
    // ---props müssen in der speziefischen route im index.js freigegeben ("props: true") werden.
    //props: ["id"]
    // ---Alternative zu props-Variante---
    // data() {
    //     return {
    //         id: this.$route.params.id
    //     }
    // }
}

</script>