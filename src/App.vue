<template>
<div id="app">
    <div>
        <p>Name: {{ name }}</p>
        <p>Address: {{ address }}</p>
        <p>DOB: {{ dob }}</p>
        <button @click="calculateAge">Calculate Age</button>
        <p>Age: {{ age }}</p>
    </div>
    <div>
        <p v-if="age < 18" class="error">You are underage.</p>
        <p v-else class="success">You are ok to use the website.</p>
        <button @click="validateAge">Validate Age</button>
    </div>
    <div v-for="user in userName" :key="user.name">
        <img :src="user.picture" />
        <h2>
            Name: {{ user.name }} <br />
            Age: {{ user.age }}
        </h2>
    </div>
</div>
</template>

<script>
export default {
    name: "App",
    data() {
        return {
            name: "John",
            address: "India",
            dob: "01/01/2003",
            age: "",
            userName: [{
                    name: "XYZ",
                    age: 20,
                    picture: "https://cdn-icons-png.flaticon.com/512/3135/3135715.png"
                },
                {
                    name: "PQR",
                    age: 25,
                    picture: "https://cdn-icons-png.flaticon.com/512/3135/3135715.png"
                },
            ],
        };
    },

    methods: {
        calculateAge() {
            this.age = new Date().getFullYear() - new Date(this.dob).getFullYear();
        },
        validateAge() {
            if (this.age < 18) {
                this.age = "You are underage.";
            } else {
                this.age = "You are ok to use the website.";
            }
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    text-align: center;
    margin-top: 50px;
}

button {
    width: 150px;
    height: 40px;
    border-radius: 20px;
    font-size: 16px;
}

div {
    margin-top: 10px;
}

.error {
    color: red;
}

.success {
    color: green;
}

img {
    width: 200px;
}
</style>
