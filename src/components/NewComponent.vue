<template>
<h1>Name:{{name }}</h1>
<h1>Email:{{email}}</h1>
<h1>{{ getAtta().name }}.<br>.{{ getAtta().email }}</h1>
<button v-on:click="showdata()">click now</button>
<button v-on:dblclick="showdata('secound button double clicked')">click now</button>

{{ count }}
</template>

 
<script>
export default {

    data() {
      return{
        count:0
    }
    },
    
    methods: {
        getAtta() {
            return {
                name: "Atta ur rahman",
                email: "mailtoattaurrahman@gmail.com"
            }
        },
        showdata() {
            alert(this.count += 1);

        }
    }

}
</script>

<style>

</style>
