<script>
export default {
    data(){
        return{
            title: "",
            detail: ""
        }
    },
    methods: {
        addProject(){
            fetch("http://localhost:3000/projects" , {
                method : "POST",
                headers : {
                    "Content-Type" : "application/json"
                },
                body : JSON.stringify({
                    title : this.title,
                    detail : this.detail,
                    complete:false
                })
            })
            .then(() => {
                this.$router.push({ name : "home" })
            })
        }
    }
}
</script>

<template>
    <div>
    <h1>Add Project</h1>
    <form @submit.prevent="addProject">
        <label>Project Title</label>
        <input type="text" v-model="title">
        <label>Project Detail</label>
        <input type="text" v-model="detail">
        <button>Add Project</button>
    </form>
    </div>
</template>



<style>
form{
    background-color:#181818;
    padding: 20px;
    border-radius: 10px;
}
label{
    display: block;
    color: #bbb;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 20px 0px 10px 0px;
}
input{
    padding: 10px;
    border: 0;
    border-bottom: 1px solid #ddd;
    width: 100%;
    box-sizing: border-box;
    height: 100px;
}
textarea{
    padding: 10px;
    border: 1px solid #ddd;
    width: 100%;
    box-sizing: border-box;
    height: 100px;
}
form button{
    display: block;
    margin: 30px auto;
    background: rgb(22, 222, 155);
    color: rgb(56, 56, 56);
    padding: 20px;
    border: 0;
    border-radius: 6px;
    font-size: 16px;
}
</style>