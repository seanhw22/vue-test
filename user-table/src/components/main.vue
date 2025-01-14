<template>
    <div class="container">
        <input type="text" v-model="search.username" placeholder="Search Username">
        <input type="text" v-model="search.phone" placeholder="Search Phone">
        <input type="text" v-model="search.email" placeholder="Search Email">
        <input type="text" v-model="search.date" placeholder="Search Register Date">
        <input type="text" v-model="search.status" placeholder="Search Status">
        <table class="table">
            <thead>
                <tr>
                    <th style="width: 5%;" scope="col">#</th>
                    <th scope="col">Username</th>
                    <th scope="col">Phone</th>
                    <th scope="col">Email</th>
                    <th scope="col">Register Data</th>
                    <th scope="col">Status</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(user,index) in filteredUsers" :key="user.username">
                    <td style="width: 5%;">{{ index + 1 }}</td>
                    <td>{{ user.username }}</td>
                    <td>{{ user.phone }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.registerDate }}</td>
                    <td>{{ user.status ? 'Active' : 'Inactive' }}</td>
                </tr>
            </tbody>
        </table>
        </div>
</template>
<script>
    export default {
        name: 'MainContent',
        props: {
        },
        data() {
            return {
                search: {
                    username: '',
                    phone: '',  
                    email: '',
                    registerDate: '',
                    status: '',
                },
            users: [] // Data is initialized as empty
            }
        },
        created() {
            // Fetch or assign data from another source
            this.fetchUsers();
        },
        methods: {
            fetchUsers() {
                if (this.users.length === 0) {
                // Simulated fetching data (replace with an API call or other data source)
                this.users = [
                    { username: 'john_doe', phone: '1234567890', email: 'john@example.com', registerDate: '2024-01-01', status: true },
                    { username: 'jane_doe', phone: '9876543210', email: 'jane@example.com', registerDate: '2024-02-15', status: false },
                    { username: 'mark_smith', phone: '5551234567', email: 'mark@example.com', registerDate: '2024-03-10', status: true }
                ];
                }
            }
        },
        computed: {
            filteredUsers() {
                return this.users.filter(user => {
                    return (
                        (this.search.username === '' || user.username.toLowerCase().includes(this.search.username.toLowerCase())) &&
                        (this.search.phone === '' || user.phone.includes(this.search.phone.replace(/\D/g, ''))) &&
                        (this.search.email === '' || user.email.toLowerCase().includes(this.search.email.toLowerCase())) &&
                        (this.search.registerDate === '' || user.registerDate.includes(this.search.registerDate)) &&
                        (this.search.status === '' || user.status === (this.search.status.toLowerCase() === 'active'))
                    );
                });
            }
        }
    }
</script>

<style scoped>
    .container input {
        margin: 10px;
        padding: 5px;
        width: calc(100% - 20px);
    }
    .container {
        height: fit-content;
        display: block;
        width: 100%;
        background-color: aquamarine;
    }
    .table {
        border: black solid 3px;
        border-block: black solid 3px;
        border-collapse: collapse;
        margin: 10px;
        width: calc(100% - 20px);
    }
    .table th, .table td {
        border: black solid 3px;
        width: 19%;
    }
</style>
