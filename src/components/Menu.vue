<template>

<div class="row">
  <div class="menu">
    <table>
      <tr>
        <th>Size</th>
        <th>Price</th>
        <th>Add</th>
      </tr>
      <tbody v-for="item in menuItems" :key="item">
        <tr>
          <td><strong>{{ item.name }}</strong></td>
        </tr>
        <tr v-for="option in item.options" :key="option">
          <td>{{ option.size }}</td>
          <td>{{ option.price / 100 }}</td>
          <td><button type="button" name="button" @click="addToBasket(item, option)">+</button></td>
        </tr>

      </tbody>
    </table>
  </div>
  <div class="basket">
    <table>
      <tr><th>Quantity</th><th>Item</th><th>Total Price</th></tr>
      <tbody v-for="item in basket" :key="item">
        <tr>
          <td>
            <button type="button" name="button" @click="decreaseQuantity(item)">-</button>
            <span>{{ item.quantity }}</span>
            <button type="button" name="button" @click="increaseQuantity(item)">+</button>
          </td>
          <td>{{ item.name }} {{ item.size}}</td>
          <td>{{ item.price * item.quantity / 100 }}</td>
        </tr>
      </tbody>
    </table>
    <p>Order total: {{ calcTotal() / 100 }}</p>
    <button type="button" name="button" class="place-btn">Checkout</button>
  </div>
</div>
</template>

<script type="text/javascript">
export default {
  data() {
    return {
      basket: [],
      basketText: 'Your basket is empty',
      menuItems: {
        1: {
          'name': 'Margherita',
          'description': 'A delicious tomato based pizza topped with mozzarella',
          'options': [{
            'size': 9,
            'price': 695
          }, {
            'size': 12,
            'price': 1095
          }]
        },
        2: {
          'name': 'Pepperoni',
          'description': 'A delicious tomato based pizza topped with mozzarella and pepperoni',
          'options': [{
            'size': 9,
            'price': 795
          }, {
            'size': 12,
            'price': 1295
          }]
        },
        3: {
          'name': 'Ham and Pineapple',
          'description': 'A delicious tomato based pizza topped with mozzarella, ham and pineapple',
          'options': [{
            'size': 9,
            'price': 795
          }, {
            'size': 12,
            'price': 1295
          }]
        }
      }
    }
  },
  methods: {
    addToBasket(item, option) {

      var exist = this.basket.find(o => o.name === item.name && o.size === option.size)
      if (exist != undefined) {
        exist.quantity++;
        return;
      }

      this.basket.push({
        name: item.name,
        price: option.price,
        size: option.size,
        quantity: 1
      });
    },
    removeFromBasket(item) {
      this.basket.splice(this.basket.indexOf(item), 1);
    },
    increaseQuantity(item) {
      item.quantity++;
    },
    decreaseQuantity(item) {
      item.quantity--;
      if (item.quantity === 0) {
        this.removeFromBasket(item);
      }
    },
    calcTotal() {
      var total = 0;
      this.basket.forEach(item => {
        total += item.price * item.quantity;
      })
      return total;
    }
  }
}
</script>

<style>
.row {
  display: flex;
}
@media only screen and (max-width: 640px) {
  .row {
    flex-direction: column;
  }
}
.menu, .basket {
  width: 50%;
  padding: 15px;
  text-align: left;
}
@media only screen and (max-width: 640px) {
  .menu, .basket {
    width: 100%;
    padding: 0;
  }
}
.menu table, .basket table {
  width: 100%;
  border-collapse: collapse;
}
.menu table th, .basket table th {
  background-color: #eceeef;
  color: #464a4c;
  padding: .75em;
}
.menu table td, .basket table td {
  color: #464a4c;
  padding: .75em;
}
.menu table td strong {
  text-transform: uppercase;
}
.menu button {
  color: #5cb85c;
  border: 1px solid #5cb85c;
  background-color: transparent;
  padding: .25rem .5rem;
  font-size: .875rem;
  border-radius: .2rem;
  vertical-align: middle;
  line-height: 1.25;
  cursor: default;
}
.basket button {
  background-color: transparent;
  padding: 0 .5rem;
  font-size: 1rem;
  line-height: 1rem;
  cursor: default;
  border: none;
}
* {
  outline: none;
}
.basket .place-btn {
  background-color: #5cb85c;
  color: #fff;
  width: 100%;
  border-radius: .2rem;
  font-size: 1rem;
  line-height: 1.25;
  padding: .25rem .5rem;
}
@media only screen and (max-width: 640px) {
  .basket .place-btn {
    margin: 0 auto 40px;
    width: 80%;
    display: block;
  }
}
.basket p {
  padding: 12px;
}
</style>
