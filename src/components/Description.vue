<template>
    <div class="flexing">
        <div class="pendingbox">
            <div class="des">
                <div><h2>Ongoing State</h2></div>
            </div>   
        </div>
        <div class="completebox">
            <div class="des">
                <div><h2>Complete State</h2></div>
            </div>   
        </div>
    </div>
</template>

<style>
.pendingbox {
    width: 180px;
    border-left: 10px solid #747474;
    text-align: center;
    padding: 8px;
    font-size: 12px;
    background-color: white;
    margin: 6px;
    margin-top: 50px;
    margin-right: 20px; 

}
.completebox {
    width: 180px;
    border-left: 10px solid rgb(22, 222, 155);
    text-align: center;
    padding: 8px;
    font-size: 12px;
    background-color: white;
    margin: 6px;
}
.flexing {
    display: flex;
    align-items: flex-end;
    flex-wrap: wrap;
    justify-content: flex-end;
    margin-bottom: 20px;
} 


</style>