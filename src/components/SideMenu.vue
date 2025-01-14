<template>
    <div class="side-menu">
        <nav class="nav flex-column">
            <a class="nav-link" href="#">Dashboard</a>
            <a class="nav-link active" aria-current="page" href="#">Users</a>
            <a class="nav-link" href="#">Settings</a>
            <a class="nav-link" href="#">Logout</a>
        </nav>
    </div>
</template>
<script>
export default {
  name: 'SideMenu',
  props: {
  },
}
</script>

<style scoped>
    .side-menu {
        width: 10%;
        align-items: flex-start;
        background-color: rgb(75, 75, 77);
        padding-left: 5px;
        box-sizing: border-box;
    }
</style>
