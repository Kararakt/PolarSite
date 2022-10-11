<script lang="ts" setup>
function Active() {
  document.getElementById("header")!.classList.toggle("active");
  document.getElementById("menu")!.classList.toggle("active");
}

document.onclick = function (e: any) {
  if (e.target.id !== "header" && e.target.id !== "menu") {
    document.getElementById("header")!.classList.remove("active");
    document.getElementById("menu")!.classList.remove("active");
  }
};
</script>
<template>
  <div class="bg-[#F2CEDA]">
    <div
      class="container mx-auto flex items-center justify-between main-div--Header"
    >
      <el-image src="/src/assets/logo_header.png" class="h-[5rem] w-[5rem]" />
      <div id="menu" @click="Active()">
        <ul
          class="flex items-center gap-6 text-[#150101] text-lg font-bold ul--Header"
        >
          <li class="cursor-pointer hover:text-[#D23166]">
            <a href="#Home">Home</a>
          </li>
          <li class="cursor-pointer hover:text-[#D23166]">
            <a href="#Products">Products</a>
          </li>
          <li class="cursor-pointer hover:text-[#D23166]">
            <a href="#Pricing">Pricing</a>
          </li>
          <li class="cursor-pointer hover:text-[#D23166]">
            <a href="#Order">Order</a>
          </li>
          <li class="cursor-pointer hover:text-[#D23166]">
            <a href="#ContactUs">Contact Us</a>
          </li>
        </ul>
      </div>
      <button class="btn--Header btn-mar--Header">Buy Now</button>
      <div id="header" @click="Active()"></div>
    </div>
  </div>
</template>
