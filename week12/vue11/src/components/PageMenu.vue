<template>
    <div class="pageMenu">
        <aside>
            <nav class="menu">
                <li>menu1</li>
                <li>menu2</li>
                <li>menu3</li>
            </nav>
        </aside>
    </div>
</template>

<script>
export default {
  name: 'PageMenu'
}
</script>

<style>
aside {
    height: 100%;
    width: 200px;
    background-color: #42b983;
}

.menu li {
    list-style: none;
    margin-top: 5px;
    font-size: 20px;
}

.menu li:hover {
    font-size: 24px;
}
</style>
