<template>
    <h1>Edit Project</h1>
    <form @submit.prevent="addProject">
        <label>Project Title</label>
        <input type="text" v-model="title">
        <label>Project Detail</label>
        <textarea cols="30" rows="10" v-model="detail"></textarea>
        <button @click="updateProject">Update Project</button>
    </form>
</template>

<script>
export default {
    props: ["id"],
    data() {
        return {
            title: "",
            detail: "",
        }
    },
    mounted() {
        fetch("http://localhost:3000/projects/" + this.id)
            .then((response) => {
                return response.json();
            })
            .then((project) => {
                this.title = project.title,
                    this.detail = project.detail
            })
            .catch((err) => {
                console.log(err.message);
            });
    },
    methods: {
        updateProject() {
            fetch("http://localhost:3000/projects/" + this.id, {
                method: "PATCH",
                headers: {
                    "Content-type": "application/json"
                },
                body: JSON.stringify(
                    {
                        title: this.title,
                        detail: this.detail
                    }
                )
            })
                .then(() => {
                    this.$router.push("/");
                });
        }
    }
}
</script>

<style></style>