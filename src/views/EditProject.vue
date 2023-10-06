<script>
export default {
    props : ["id"],
    data(){
        return{
            title : "",
            detail : ""

        }
    },
    mounted(){
        fetch("http://localhost:3000/projects/" + this.id )
        .then((res) => {
            return res.json()
        })
        .then((datas) => {
            this.title = datas.title
            this.detail = datas.detail
        })
    },
    methods:{
        updatepj(){
            fetch("http://localhost:3000/projects/" + this.id , {
                method:"PATCH",
                headers : {
                    "Content-Type" : "application/json"
                },
                body : JSON.stringify({
                    title : this.title,
                    detail : this.detail,
                })
            })
            .then((res) => {
                this.$router.push({ name : "home" })
            })
            .catch((errs) => {
                console.log(errs);
            })
        }
    }
}
</script>

<template>
    <div>
        <h1>Edit Project</h1>
        <form @submit.prevent="addProject">
        <label>Project Title</label>
        <input type="text" v-model="title">
        <label>Project Detail</label>
        <input type="text" v-model="detail">
        <button @click="updatepj">Update Project</button>
    </form>
    </div>
</template>



<style>

</style>