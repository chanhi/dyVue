<template>
  <div class="test">
      <h1>{{title}}</h1>
      <h2 v-html="htmlText"></h2>
      <div class="ta">
          <table>
            <thead>
                <tr>
                    <th>제품명</th>
                    <th>가격</th>
                    <th>카테고리</th>
                    <th>배송료</th>
                </tr>
            </thead>
            <tbody>
                <tr :key="i" v-for="(product, i) in productList">
                    <td>{{ product.product_name }}</td>
                    <td>{{ product.price }}</td>
                    <td>{{ product.category }}</td>
                    <td>{{product.delivery_price}}</td>
                </tr>
            </tbody>
          </table>
      </div>
      <hr>
      <input type="text" v-model="myText">
      <p>{{ myText }}</p>
      <label><input type="checkbox" value="red" v-model="myChecks">red</label><br>
      <label><input type="checkbox" value="blue" v-model="myChecks">blue</label><br>
      <label><input type="checkbox" value="green" v-model="myChecks">green</label><br>
      <p>Choosed color: {{myChecks}}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'Test Page',
      htmlText: '<p style="color:blue">v-html</p>',
      myChecks: [],
      myText: '',
      productList: [
        { product_name: '기계식키보드', price: 25000, category: '노트북/태블릿', delivery_price: 5000 },
        { product_name: '기계식키보드', price: 25000, category: '노트북/태블릿', delivery_price: 5000 },
        { product_name: '기계식키보드', price: 25000, category: '노트북/태블릿', delivery_price: 5000 },
        { product_name: '기계식키보드', price: 25000, category: '노트북/태블릿', delivery_price: 5000 },
        { product_name: '기계식키보드', price: 25000, category: '노트북/태블릿', delivery_price: 5000 }
      ]
    }
  }
}
</script>

<style scoped>
    .ta {
        width: 100%;
        display: flex;
        justify-content: center;
    }
    table{
        width: 50%;
        border-collapse: collapse;
    }
    td, th {
        border: 1px solid black;
        text-align: left;
        padding: 8px;
    }
    th {
        background-color: rgb(203, 255, 124);
    }
    td {
        background-color: rgb(223, 255, 255);
    }
    td:hover {
        background-color: aqua;
    }
</style>
