<template>
    <v-card
        class="card"
        elevation="5"
        v-on:click.prevent="navigate(faculty)"
        color="secondary"
    >
        <br />
        <v-avatar color="orange" size="85">
            <span class="text secondary--text headline font-weight-thin">{{ faculty.abbreviation }}</span>
        </v-avatar>
        <v-card-text>
            <h2 class="text title warning--text font-weight-thin">{{ faculty.name }}</h2>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: "FacultyCard",
        props: [
            'faculty',
        ],
        methods: {
            navigate(faculty) {
                this.$store.dispatch('changeFaculty', faculty);
                this.$router.push({name: 'Faculty', params: {id: faculty._id, faculty: faculty}})
            }
        },
    }
</script>

<style scoped>
    .card {
        box-shadow: rgba(0, 0, 0, 0.06) 0px 2px 4px;
        transition: all .3s ease-in-out;
        height: 230px;
    }
    .card:hover {
        transform: translate3d(0px, -18px, 0px);
        cursor: pointer;
        background-color: rgba(255, 255, 255, 0.1) !important;
    }
    .text {
        text-align: center;
        user-select: none;
    }

</style>
