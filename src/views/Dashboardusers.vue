<template>
  <body style="background-color: #cccccc">
    <div>
      <div style="display: inline-block">Deposit order</div>
      <h1 class="text-center font-bold leading-10 text-gray-800">
        {{ users }}
      </h1>
      <h1
        style="display: inline-block"
        v-for="user in orders"
        :key="user._id"
        class="text-center font-bold leading-10 text-gray-800"
      >
        {{ user.inviteId }}
      </h1>
      <div class="userId" v-for="order in orders" :key="order._id">
        {{ order.userId }}
      </div>
      <div class="inor">
        <div style="font-weight: 800">balance</div>
        <h1
          v-for="user in orders"
          :key="user._id"
          class="text-center font-bold leading-10 text-gray-800"
        >
          {{ user.balance }}
        </h1>
      </div>
      <div class="inline-block p-8 text-center">
        <div class="font-bold tracking-wide text-gray-800">
          <div class="relative">
            <div
              class="absolute text-gray-600 dark:text-gray-400 flex items-center pl-4 h-full cursor-pointer"
            >
              $
            </div>
            <input
              v-model="crdet"
              id="number"
              class="text-gray-600 dark:text-gray-800 focus:outline-none focus:border focus:border-indigo-700 dark:focus:border-indigo-700 dark:border-gray-700 dark:bg-gray-800 bg-white font-normal w-64 h-10 flex items-center pl-12 text-sm border-gray-300 rounded border shadow"
              placeholder="balance"
            />
          </div>
        </div>
        <div v-if="alertb" class="alert alert-danger" role="alert">
          {{ alertb }}
        </div>
        <button
          v-if="son === 0"
          @click="copyTestingCode"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          add now
        </button>
        <button
          v-if="son === 1"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          add now
        </button>
        <button
          v-if="sod === 0"
          @click="debtUsersbalance"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          debt
        </button>
        <button
          v-if="sod === 1"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          debt
        </button>
      </div>
      <div style="font-weight: 800">profit</div>
      <h1
        v-for="user in orders"
        :key="user._id"
        class="text-center font-bold leading-10 text-gray-800"
      >
        {{ user.profit }}
      </h1>
      <div class="inline-block p-8 text-center">
        <div class="font-bold tracking-wide text-gray-800">
          <div class="relative">
            <div
              class="absolute text-gray-600 dark:text-gray-400 flex items-center pl-4 h-full cursor-pointer"
            >
              $
            </div>
            <input
              v-model="profitcrde"
              id="number"
              class="text-gray-600 dark:text-gray-800 focus:outline-none focus:border focus:border-indigo-700 dark:focus:border-indigo-700 dark:border-gray-700 dark:bg-gray-800 bg-white font-normal w-64 h-10 flex items-center pl-12 text-sm border-gray-300 rounded border shadow"
              placeholder="profit"
            />
          </div>
        </div>
        <div v-if="alert" class="alert alert-danger" role="alert">
          {{ alert }}
        </div>
        <button
          v-if="sof === 0"
          @click="profitcrdet"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          add now
        </button>
        <button
          v-if="sof === 1"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          add now
        </button>
        <button
          @click="profitdebt"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          debt
        </button>
      </div>
      <div class="percentage">
        <div style="font-weight: 800">percentage</div>
        <h1 style="display: inline-block">%</h1>
        <h1
          style="display: inline-block"
          v-for="user in orders"
          :key="user._id"
          class="text-center font-bold leading-10 text-gray-800"
        >
          {{ user.percentage }}
        </h1>
      </div>
      <div class="inline-block p-8 text-center">
        <div class="font-bold tracking-wide text-gray-800">
          <div class="relative">
            <div
              class="absolute text-gray-600 dark:text-gray-400 flex items-center pl-4 h-full cursor-pointer"
            >
              %
            </div>
            <input
              v-model="percentageUsers"
              id="number"
              class="text-gray-600 dark:text-gray-800 focus:outline-none focus:border focus:border-indigo-700 dark:focus:border-indigo-700 dark:border-gray-700 dark:bg-gray-800 bg-white font-normal w-64 h-10 flex items-center pl-12 text-sm border-gray-300 rounded border shadow"
              placeholder="percentage"
            />
          </div>
        </div>
        <button
          @click="percentageUsersa"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          percentage
        </button>
      </div>
      <div class="percentage">
        <div style="font-weight: 800">usdtId</div>
        <h1
          style="display: inline-block"
          v-for="user in orders"
          :key="user._id"
          class="text-center font-bold leading-10 text-gray-800"
        >
          {{ user.usdtId }}
        </h1>
      </div>
      <div class="inline-block p-8 text-center">
        <div class="font-bold tracking-wide text-gray-800">
          <div class="relative">
            <input
              v-model="usdtId"
              id="number"
              class="text-gray-600 dark:text-gray-800 focus:outline-none focus:border focus:border-indigo-700 dark:focus:border-indigo-700 dark:border-gray-700 dark:bg-gray-800 bg-white font-normal w-64 h-10 flex items-center pl-12 text-sm border-gray-300 rounded border shadow"
              placeholder="usdtId"
            />
          </div>
        </div>
        <button
          @click="usdtIdUserschanhe"
          type="button"
          class="m-4 text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center mr-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
        >
          update
        </button>
      </div>
    </div>
  </body>
</template>

<script>
import AuthenticationServices from "@/services/AuthenticationServices";

export default {
  name: "MyComponent",
  data() {
    return {
      orders: [],
      users: "",
      id: "",
      crdet: "",
      usdtId: "",
      alert: "",
      alertb: "",
      percentageUsers: "",
      profitcrde: "",
      son: 0,
      sod: 0,
      sof: 0,
    };
  },
  async created() {
    this.id = this.$route.params.id;
    const orderId = this.id;
    const response = await AuthenticationServices.getUser(orderId);
    this.orders = response;
    console.log(this.orders);
  },
  methods: {
    async profitcrdet() {
      this.sof = 1;
      if (this.profitcrde <= 0) {
        this.alert = "zero or less not allawed";
      } else {
        const orderId = this.id;
        await AuthenticationServices.profitcrdet({
          userId: orderId,
          balance: this.profitcrde,
        });
        window.location.reload();
      }
    },
    async profitdebt() {
      const orderId = this.id;
      await AuthenticationServices.profitdebt({
        userId: orderId,
        balance: this.profitcrde,
      });
      window.location.reload();
    },
    async copyTestingCode() {
      this.son = 1;
      if (this.crdet <= 0) {
        this.alertb = "zero or less not allawed";
      } else {
        const orderId = this.id;
        await AuthenticationServices.crdetUsersbalance({
          userId: orderId,
          balance: this.crdet,
        });
        window.location.reload();
      }
    },
    async debtUsersbalance() {
      this.sod = 1;
      const orderId = this.id;
      await AuthenticationServices.debtUsersbalance({
        userId: orderId,
        balance: this.crdet,
      });
      window.location.reload();
    },
    async percentageUsersa() {
      const orderId = this.id;
      await AuthenticationServices.percentageUsersbalance({
        userId: orderId,
        balance: this.percentageUsers,
      });
      window.location.reload();
    },
    async usdtIdUserschanhe() {
      const orderId = this.id;
      await AuthenticationServices.usdtIdurluser({
        userId: orderId,
        balance: this.usdtId,
      });
      window.location.reload();
    },
  },
};
</script>

<style scoped>
.userId {
  position: relative !important;
  top: 8px !important;
  font-size: large;
  font-weight: bolder;
}
.inor {
  position: relative !important;
  top: 35px !important;
}
.balance {
  display: inline-block;
  position: relative;
  right: 20%;
}
.profit {
  display: inline-block;
  position: relative;
  left: 20%;
}
</style>
