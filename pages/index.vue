<template>
  <div>
    <div class="inline-block relative w-64 py-20">
      <select
        v-model="active"
        class="
          block
          appearance-none
          w-full
          bg-white
          border border-gray-400
          hover:border-gray-500
          px-4
          py-2
          pr-8
          rounded
          shadow
          leading-tight
          focus:outline-none focus:shadow-outline
        "
      >
        <option>1</option>
        <option>2</option>
      </select>
      <div
        class="
          pointer-events-none
          absolute
          inset-y-0
          right-0
          flex
          items-center
          px-2
          text-gray-700
        "
      >
        <svg
          class="fill-current h-4 w-4"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 20 20"
        >
          <path
            d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
          />
        </svg>
      </div>
    </div>
    <div class="overflow-x-auto">
      <table  class="min-w-full text-sm divide-y-2 divide-gray-200">
        <thead >
          <tr>
            <th
              class="
                px-4
                py-2
                font-medium
                text-left text-gray-900
                whitespace-nowrap
              "
            >
              Name
            </th>
            <th
              class="
                px-4
                py-2
                font-medium
                text-left text-gray-900
                whitespace-nowrap
              "
            >
             İD
            </th>
            <th
              class="
                px-4
                py-2
                font-medium
                text-left text-gray-900
                whitespace-nowrap
              "
            >
              Fee Recipient
            </th>
            <th
              class="
                px-4
                py-2
                font-medium
                text-left text-gray-900
                whitespace-nowrap
              "
            >
              Seller Fee Basis Points
            </th>
          </tr>
        </thead>

        <tbody class="divide-y divide-gray-200">
          <tr>
            <td class="px-4 py-2 font-medium text-gray-900 whitespace-nowrap">
              {{items.name}}
            </td>
            <td class="px-4 py-2 text-gray-700 whitespace-nowrap">
             {{items.token_id}}
            </td>
            <td class="px-4 py-2 text-gray-700 whitespace-nowrap">
              {{items.fee_recipient}}
            </td>
            <td class="px-4 py-2 text-gray-700 whitespace-nowrap">{{items.seller_fee_basis_points}}</td>
          </tr>

          
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      items: [],
      active:1,
    };
  },
   created: function() {
    if (this.active==1) {
        axios.get("https://deadtown.mvhq.art/internal-meta/1").then((res) => {
      this.items = res.data;
      console.log(this.items.name);
      console.log(this.active)
    });
      } 
   
  },
  
  watch: {
    
    active() {
      if (this.active==1) {
        axios.get("https://deadtown.mvhq.art/internal-meta/1").then((res) => {
      this.items = res.data;
      console.log(this.items.name);
      console.log(this.active)
    });
      } else if (this.active==2) {
       axios.get("https://deadtown.mvhq.art/internal-meta/2").then((res) => {
      this.items = res.data;
      console.log(this.items.name);
      console.log(this.active)
    });
      }
    } 
  },
  
};
</script>
