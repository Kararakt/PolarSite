<script lang="ts" setup>
import { ref, reactive } from "vue";
import type { FormInstance } from "element-plus";

const SubmitMessage = async (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  await formEl.validate((valid, fields) => {
    if (valid) {
      console.log("Submit!");
    } else {
      console.log("Error Submit!", fields);
    }
  });
};

const validateEmail = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the email"));
  } else if (value.indexOf("@") == -1) {
    callback(new Error("Please input correct adress"));
  } else if (value.indexOf(".") == -1) {
    callback(new Error("Please input correct adress"));
  } else {
    callback();
  }
};

const ruleForm = reactive({
  Email: "",
});

const rules = reactive({
  Email: [{ validator: validateEmail, trigger: "blur" }],
});
const ruleFormRef = ref<FormInstance>();
</script>
<template>
  <div class="bg-black text-white">
    <div class="container mx-auto">
      <div class="grid grid-cols-4 py-14 first-div--Footer">
        <div class="flex flex-col gap-5">
          <el-image
            src="/src/assets/logo_header.png"
            class="h-[5rem] w-[5rem]"
          />
          <div>
            Some food has looked so awful that it's looked like something that
            the dog's brought home.
          </div>
          <div class="flex flex-col gap-2 pt-2">
            <h1 class="text-lg font-medium">Follow Us</h1>
            <div class="flex gap-4">
              <a
                class="cursor-pointer"
                href="https://www.facebook.com/"
                target="_blank"
              >
                <el-image src="/src/assets/facebooklogo.png"
              /></a>
              <a
                class="cursor-pointer"
                href="https://twitter.com/"
                target="_blank"
                ><el-image src="/src/assets/twitterlogo.png"
              /></a>
              <a
                class="cursor-pointer"
                href="https://www.instagram.com/"
                target="_blank"
              >
                <el-image src="/src/assets/instagramlogo.png"
              /></a>
              <a
                class="cursor-pointer"
                href="https://www.invisionapp.com/"
                target="_blank"
                ><el-image src="/src/assets/invisionlogo.png"
              /></a>
            </div>
          </div>
        </div>
        <div
          class="flex flex-col justify-center items-center text--Footer custom-text--Footer"
        >
          <ul class="flex flex-col gap-2">
            <li><a href="#Home">Home</a></li>
            <li><a href="#Products">Product</a></li>
            <li><a href="#Pricing">Pricing</a></li>
            <li><a href="#Order">Order</a></li>
            <li><a href="#ContactUs">Contact Us</a></li>
          </ul>
        </div>
        <div
          class="flex flex-col gap-6 justify-center items-center text--Footer"
        >
          <ul class="flex flex-col gap-2">
            <li class="cursor-pointer"><a>Delivery Information</a></li>
            <li class="cursor-pointer"><a>Privacy Policy</a></li>
            <li class="cursor-pointer"><a>Terms & Condition</a></li>
            <li class="cursor-pointer"><a>Search Terms</a></li>
            <li class="cursor-pointer"><a>Order & Return</a></li>
          </ul>
        </div>
        <div class="flex flex-col gap-4 justify-center items-start">
          <h1 class="text-lg">Newsletter</h1>
          <el-form ref="ruleFormRef" :model="ruleForm" :rules="rules"
            ><div class="flex form--Footer">
              <el-form-item prop="Email"
                ><el-input
                  placeholder="Your Email"
                  class="pb-2"
                  v-model="ruleForm.Email"
                  ><template #append>
                    <div
                      class="cursor-pointer"
                      @click="SubmitMessage(ruleFormRef)"
                    >
                      Subscribe
                    </div>
                  </template></el-input
                ></el-form-item
              >
            </div></el-form
          >
          <div class="flex gap-4">
            <el-image
              src="/src/assets/paypallogo.png"
              class="h-auto w-auto cursor-pointer"
            />
            <el-image
              src="/src/assets/mastercardlogo.png"
              class="h-auto w-auto cursor-pointer"
            />
            <el-image
              src="/src/assets/visalogo.png"
              class="h-auto w-auto cursor-pointer"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
