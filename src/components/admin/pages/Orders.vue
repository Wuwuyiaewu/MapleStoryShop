<template>
  <div class="py-4">
    <loading :active.sync="isLoading">
      <template slot="default">
        <div class="loading-image"></div>
      </template>
    </loading>
    <table class="table mt-4" v-if="orders.length">
      <thead class="thead-light">
        <tr>
          <th>購買時間</th>
          <th>Email</th>
          <th>購買款項</th>
          <th>應付金額</th>
          <th>是否付款</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in sortOrder" :key="item.id" :class="{'text-secondary': !item.is_paid}">
          <td class="align-middle">{{ item.create_at | date }}</td>
          <td class="align-middle">
            <span v-text="item.user.email" v-if="item.user"></span>
          </td>
          <td class="align-middle">
            <ul class="list-unstyled mt-auto mb-auto">
              <li v-for="(product, i) in item.products" :key="i">
                {{ product.product.title }} 數量：{{ product.qty }}
                {{ product.product.unit }}
              </li>
            </ul>
          </td>
          <td class="align-middle text-right">{{ item.total | currency }}</td>
          <td class="align-middle">
            <span v-if="item.is_paid" class="text-success">已付款</span>
            <span v-else class="text-danger">尚未啟用</span>
          </td>
        </tr>
      </tbody>
    </table>
    <!-- 分頁 -->
    <Pagination v-bind:childPaginations="pagination" @changeCurrentPage="getOrders"></Pagination>
  </div>
</template>

<script>
import $ from "jquery";
import Pagination from "../../Pagination";

export default {
  data() {
    return {
      orders: [],
      pagination: {},
      isLoading: false
    };
  },
  components: {
    Pagination
  },
  methods: {
    getOrders(currentPage = 1) {
      const vm = this;
      const api = `${process.env.APIPATH}/api/${process.env.CUSTOMPATH}/admin/orders?page=${currentPage}`;
      // console.log(process.env.APIPATH, process.env.CUSTOMPATH);
      vm.isLoading = true;
      this.$http.get(api).then(response => {
        vm.isLoading = false;
        vm.orders = response.data.orders;
        vm.pagination = response.data.pagination;
        // console.log(response.data);
      });
    }
  },
  computed: {
    sortOrder() {
      const vm = this;
      let newOrder = [];
      if (vm.orders.length) {
        newOrder = vm.orders.sort((a, b) => {
          const aIsPaid = a.is_paid ? 1 : 0;
          const bIsPaid = b.is_paid ? 1 : 0;
          return bIsPaid - aIsPaid;
        });
      }
      return newOrder;
    }
  },
  created() {
    this.getOrders();
  }
};
</script>

<style scoped lang="scss">
.loading-image {
  background-image: url(../../../assets/images/GIFs/KingSlime.gif);
  background-size: cover;
  width: 219px;
  height: 230px;
}
</style>
