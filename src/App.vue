<template>
<div id="app" class="container">
    <div class="content-box">
        <div class="profile-wrap">
        <div class="profile"></div>
        </div>
    </div>
    <router-view/>
</div>
</template>

<script>
export default { 
    data() {
        return {
            title:'title',
            items: [
                { 
                    title: '코딩 강의',
                    start_date: '2022.03.20'
                },
                { 
                    title: '물 2L',
                    start_date: '2022.03.18'
                },
            ],
        };
    },
}
</script>

<style>
#app {
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
/* text-align: center; */
}

* {
box-sizing: border-box;
padding: 0;
margin: 0;
}

ul li {
    list-style: none;
}

button {
    border: none;
}

nav {
    padding: 30px;
}

nav a {
    font-weight: bold;
    color: #2c3e50;
}

nav a.router-link-exact-active {
    color: #42b983;
}

body {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background: #eee;
}

.container {
    display: flex;
    width: 1440px;
    height: 720px;
    background: #f6f6f6;
    border-radius: 0.5rem;
    box-shadow: 0px 0px 15px rgba(0,0,0,0.05);
}

.content-box {
    flex: 0 0 50%;
    padding: 3rem;
}

.content-box h2 {
    margin-bottom: 2rem;
}

.content-item {
    font-size: 1rem;
    font-weight: 600;
    background: #fff;
    border-radius: 0.5rem;
    padding: 1rem 1.25rem;
    margin-bottom: 1rem;
}

.content-item a {
    cursor: pointer;
}

.content-item .start-date {
    font-size: 0.875rem;
    color: #999;
}


/* profile */

.profile-wrap {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 4rem;
    width: 100%;
    height: 100%;
}

.profile {
    width: 100%;
    padding-bottom: 100%;
    border-radius: 50%;
    background: #fff;
    margin: auto;
}

/* button */

.btn-primary {
    display: block;
    font-size: 1rem;
    font-weight: 700;
    width: 100%;
    padding: 1.25rem 0;
    border-radius: 0.5rem;
    color: #fff;
    text-align: center;
    text-decoration: none;
    background: #6FA2EF;
    margin-top: 2rem;
}

/* input */
input[type="text"] {
    font-size: 1rem;
    border-radius: 0.5rem;
    border: 2px solid #999;
    width: 100%;
    padding: 1rem;
}

/* calendar */
.vc-container.vc-is-expanded {
    border: none;
    background: none;
    padding-top: 30px;
}

.vc-container * {
    text-align: center;
}

.vc-weekday {
    padding: 20px 0 !important;
}

.day-content {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 80px;
    cursor: pointer;
}

.day-label {
    position: relative;
    z-index: 5;
    line-height: 1.4;
}

.day-circle {
    width: 50%;
    padding-bottom: 50%;
    border-radius: 50%;
    position: absolute;
    z-index: 1;
}

.day-circle.on {
    background: #6FA2EF;
}

.day-circle.on + .day-label {
    color: #fff;
}

.vc-day {
    height: 60px !important;
}

</style>
