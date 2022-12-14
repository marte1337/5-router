<template>
    <h1>Jobs</h1>
    <!-- v-if = optionale Anzeige während des fetch, gegenüber dem JobDetails Comp hier "jobs.lenght", weil
    "jobs" ist hier nicht "null", sondern hat "[]" (also quasi "Array") als Value, daher also "kein leeres Array"
    als Prämisse -->
    <div v-if="jobs.length">
        <div v-for="job in jobs" :key="job.id" class="job">
        <router-link :to="{ name: 'jobDetails', params: { id: job.id } }">
            <h2> {{ job.title }} </h2>
        </router-link>
        </div>
    </div>
    <div v-else>Loading jobs...</div>
</template>



<script>
export default {
    data() {
        return {
            jobs: []
            // --- VERSION 1, dieser Content wird in V2 aus db.json abgeholt und in das Data-Objekt "jobs" oben eingespeist---
            // jobs : [
            //     { title: "Frontend-Dev", id: 1, details: "lorem"},
            //     { title: "Backend-Dev", id: 2, details: "lorem"},
            //     { title: "Vue-Dev", id: 3, details: "lorem"},
            // ]
        }
    },
    mounted() {
        fetch("http://localhost:3000/jobs")
        .then(res => res.json())
        .then(content => this.jobs = content)
        .catch(err => console.log(err.message))
    }
}

</script>


<style>

.job h2 {
background: #f4f4f4;
padding: 20px;
border-radius: 10px;
margin: 10px auto;
max-width: 600px;
cursor: pointer;
color: #444;
}

.job h2:hover {
background: #ddd;
}

.job a {
text-decoration: none;
}

button {
margin: 0 10px;
padding: 10px;
border: none;
border-radius: 4px;
}

</style>