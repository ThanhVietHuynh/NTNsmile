<script >

export default {
    data () {
        const token = localStorage.getItem("token");
        
        return {
            shouldDisplayBtn: !!token,
        }
    },
    mounted: function () {
        this.$router.afterEach(() => {
            const token = localStorage.getItem("token");
            this.shouldDisplayBtn = !!token;
        });
    },
    methods : {
        btnDeco: function () {
            this.shouldDisplayBtn = false;
            localStorage.clear();
        },
    },  
  
}
</script>

<template>
    <button v-if="shouldDisplayBtn" class="btn-deco" @click="btnDeco">Deconnexion</button>
</template>

<style scoped>
.btn-deco{
    border: none;
    border-radius: 4px;
    cursor: pointer;
    background-color: #eb6c31;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
}
.btn-deco:hover{
    background-color: #a85027;
    transition: 0.3s;
}

</style>
