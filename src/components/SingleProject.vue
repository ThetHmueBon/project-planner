<template>
    <div class="project" :class="{complete : project.complete}">
        <div class="flexbox">
            <div><h2 @click="showDetail =! showDetail">{{ project.title }}</h2></div>
            <div>
                <span class="material-symbols-outlined" @click="delpj">
            delete
        </span>

        <router-link :to="{ name : 'EditProject' , params: { id : project.id } }">
            <span class="material-symbols-outlined">
                edit
            </span>
        </router-link>
        
        <span class="material-symbols-outlined" @click = "completepj">
            done
        </span>
            </div>
        </div>
        <p v-if="showDetail">{{ project.detail }}</p>
        <!-- {{project.complete}} -->
    </div>
</template>


<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail : false,
            api : 'http://localhost:3000/projects',
        }
    },
    methods : {
        delpj(){
            // alert(this.api + "/"+ this.project.id , {method:'DELETE'})
            let delRoute = this.api + "/"+ this.project.id;
            fetch( delRoute , { method :'DELETE' })
            .then(() => {
                this.$emit("delete" , this.project.id)
            })
            .catch((errs) => {
                alert(
                    errs
                );
            })
        },
        completepj(){
            let completeRoute =  this.api+ "/"+this.project.id;
            fetch(completeRoute , {
                method : "PATCH" ,
                headers : {
                    "Content-Type" : "application/json"
                },
                body : JSON.stringify({
                    complete:!this.project.complete
                })
            })
            .then(() => {
                this.$emit("complete" , this.project.id);
            })
            .catch((errs) => {
                alert(errs);
            })
        }
    }
}
</script>

<style>
    .project{
        border-left: 7px solid #747474;
        padding: 30px;
        /* background-color: rgb(22, 222, 155); */
        background-color: white;
        margin: 10px;
        border-radius: 7px;
    }
    h2{
        cursor: pointer;
        color:#5d5b5b;
        font-weight: 550;
    }
    p{
        color:#233329;
    }
    .flexbox{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    span{
        margin-left: 10px;
        /* color: black; */
        color: rgb(12, 104, 73);
    }
    span:hover{
        color: #777;
        cursor: pointer;
    }
    .complete{
        border-left-color: rgb(22, 222, 155);
    }
</style>