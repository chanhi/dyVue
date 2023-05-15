<template>
    <div class="Rad">
        <label><input type="radio" value="red" v-model="picked">red</label><br>
        <label><input type="radio" value="blue" v-model="picked">blue</label><br>
        <label><input type="radio" value="green" v-model="picked">green</label><br>
        <p>Choosed color: {{picked}}</p>
    </div>
</template>

<script>
export default {
  data () {
    return {
      picked: 'red'
    }
  }
}
</script>
