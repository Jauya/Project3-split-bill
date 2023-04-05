<script setup>
import { ref } from "vue";
import {  pay } from "../store/store";

const props = defineProps(["id", "numberOfPerson", "totalPerPerson", "paid"]);
let paid = ref(false);

function handleChange(e){
    paid = e.target.checked;

    pay(props.id, paid)
}
</script>
<template>
    <div :class = '["person",props.paid ? "person-paid" : "person-no-paid"]'>
        <div class="person-number">
            Person {{ props.numberOfPerson }}
        </div>
        <div class="person-to-pay">
            {{ 
            new Intl.NumberFormat("en-US", {
                style: "currency",
                currency: "USD",
            }).format(props.totalPerPerson)
            }}
        </div>
        <div class="paid">
            <input type="checkbox" @change = "handleChange"> Paid
        </div>
    </div>
</template>
<style scoped>
    .person{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #242424;
        border-radius: 5px;
    }
    .person-paid{
        border: solid 3px yellowgreen;
    }
    .person-no-paid{
        border: solid 3px rgb(180, 180, 180);
    }
    .person-number{
        background-color: #181818;
        padding: 10px;
        font-weight: 600;
        color: rgb(255, 255, 255);
        text-align: center;
    }
    .person-to-pay{
        text-align: center;
        font-size: 30px;
        font-weight: bolder;
        color:yellowgreen;
        padding-block: 40px;
    }
    .paid{
        background-color: #363636;
        padding: 10px;
    }
</style>