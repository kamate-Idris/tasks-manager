<template>
    <footer>
        <h5>Copyright &copy; 2023</h5>
        <router-link to="/about">About</router-link>
    </footer>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style scoped>
footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    gap: 5px;
}
</style>