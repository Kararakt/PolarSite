<script setup lang="ts">
import TabsItem from "../components/TabsItem.vue";
import type { FormInstance } from "element-plus";
import { ref, reactive } from "vue";

const items = [
  {
    id: 1,
    src: "/src/assets/first_icon.png",
    title: "Free Shipping",
    description: "Last Chance! Free shipping on all orders ends today.",
  },
  {
    id: 2,
    src: "/src/assets/second_icon.png",
    title: "Quick Packaging",
    description: "Last Chance! Free shipping on all orders ends today.",
  },
  {
    id: 3,
    src: "/src/assets/third_icon.png",
    title: "100% Money Back",
    description: "Last Chance! Free shipping on all orders ends today.",
  },
  {
    id: 4,
    src: "/src/assets/fourth_icon.png",
    title: "Fast Delivery",
    description: "Last Chance! Free shipping on all orders ends today.",
  },
];

const photos = [
  {
    id: 1,
    src: "/src/assets/icon1_order.png",
    title: "Select Your Food",
  },
  {
    id: 2,
    src: "/src/assets/icon2_order.png",
    title: "Add To Cart",
  },
  {
    id: 3,
    src: "/src/assets/icon3_order.png",
    title: "Order Your Food",
  },
];

const validatePhone = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the phone"));
  } else if (isValidPhone(value) === false) {
    callback(new Error("Please input the correct phone"));
  } else {
    callback();
  }
};

const validateQuestion = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input your question"));
  }
};

const validateTextArea = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please, input description for your problem"));
  }
};

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

const ruleFormRef = ref<FormInstance>();

const ruleForm = reactive({
  Phone: "",
  Question: "",
  TextArea: "",
});

const rules = reactive({
  Phone: [{ validator: validatePhone, trigger: "blur" }],
  Question: [{ validator: validateQuestion, trigger: "blur" }],
  TextArea: [{ validator: validateTextArea, trigger: "blur" }],
});

function isValidPhone(string: any) {
  let res = string.match(
    /^(\+{1}\d{2,3}\s?[(]{1}\d{1,3}[)]{1}\s?\d+|\+\d{2,3}\s{1}\d+|\d+){1}[\s|-]?\d+([\s|-]?\d+){1,2}$/
  );
  return res !== null;
}

function scrollUpFunction() {
  document.body.scrollTop = 0;
  document.documentElement.scrollTop = 0;
}

window.onscroll = function () {
  scrollFunction();
};
function scrollFunction() {
  if (
    document.body.scrollTop > 200 ||
    document.documentElement.scrollTop > 200
  ) {
    document.getElementById("iconUp")!.style.display = "block";
  } else {
    document.getElementById("iconUp")!.style.display = "none";
  }
}
</script>

<template>
  <div>
    <div class="bg-[#F2CEDA]">
      <div class="container mx-auto grid grid-cols-2 first-div--HomePage">
        <div class="flex flex-col justify-center gap-6 items-start">
          <div class="flex flex-col gap-4">
            <div class="text-[#0F0101]">Sweet fun, full of milk.</div>
            <h1 class="text-[3.5rem] leading-none first-title--HomePage">
              Feel inside cold with our delicious
              <i class="text-[#D23166]">ice-cream.</i>
            </h1>
          </div>
          <div class="text-lg">
            Some food has looked so awful that it's looked like something that
            the dog's brought home, yet after one mouthful I've been left eating
            my thoughts, my words.
          </div>
          <button class="btn--Header btn-cer--HomePage">Buy Now</button>
        </div>
        <el-image
          src="/src/assets/home_pic1.png"
          class="h-auto w-auto"
          id="Home"
        />
      </div>
    </div>
    <div class="container mx-auto py-16">
      <div class="grid grid-cols-4 gap-8 card--HomePage">
        <el-card v-for="item in items" :key="item.id" shadow="hover"
          ><div class="flex flex-col items-center text-center gap-2">
            <el-image :src="item.src" />
            <h1 class="text-xl font-semibold pt-4">{{ item.title }}</h1>
            <div class="text-sm">{{ item.description }}</div>
          </div></el-card
        >
      </div>
    </div>
    <div class="bg-[#F2CEDA]">
      <div class="container mx-auto grid grid-cols-2 second-div--HomePage">
        <div class="flex flex-col justify-center items-start gap-6">
          <h1
            class="text-[2.5rem] text-[#150101] font-semibold second-title--HomePage"
          >
            Brown Sugar Oatmea
          </h1>
          <div>
            Together with McDonald’s, Burger King has grown to become synonymous
            with burgers in the US. Together with McDonald’s, Burger King has
            grown to become synonymous.
          </div>
          <button class="btn--Header btn-cer--HomePage">See Details</button>
        </div>
        <el-image src="/src/assets/home_pic2.png" class="h-auto w-auto" />
      </div>
    </div>
    <div class="container mx-auto pt-32" id="Products">
      <h1 class="text-[2.5rem] flex justify-center">Our Products</h1>
      <div class="main-div-tabs--HomePage py-36">
        <el-tabs type="border-card" id="Pricing">
          <el-tab-pane
            ><template #label
              ><span class="text-lg YYYYY">ICE CREAM</span></template
            ><TabsItem />
          </el-tab-pane>
          <el-tab-pane
            ><template #label
              ><span class="text-lg">CAYENNE CHOCOLATE</span></template
            >
            <TabsItem
          /></el-tab-pane>
          <el-tab-pane
            ><template #label
              ><span class="text-lg">CAKE BATTER</span></template
            >
            <TabsItem
          /></el-tab-pane>
          <el-tab-pane
            ><template #label><span class="text-lg">CANDY CANE</span></template>
            <TabsItem
          /></el-tab-pane>
          <el-tab-pane
            ><template #label><span class="text-lg">PLATTERS</span></template>
            <TabsItem
          /></el-tab-pane>
          <el-tab-pane
            ><template #label><span class="text-lg">DESSERT</span></template>
            <TabsItem
          /></el-tab-pane>
        </el-tabs>
      </div>
    </div>
    <div class="bg-[#F2CEDA]">
      <div
        class="container mx-auto grid grid-cols-2 py-10 justify-items-center items-center third-div--HomePage"
        id="Order"
      >
        <el-image src="/src/assets/home_pic3.png" class="h-[34rem] w-[17rem]" />
        <div class="flex flex-col gap-6 first-text--HomePage">
          <h1 class="text-[2.5rem] leading-none">
            Simple Way To Order Your Food
          </h1>
          <div>
            Some food has looked so awful that it's looked like something that
            the dog's brought home, yet after one mouthful I've been left eating
            my thoughts.
          </div>
          <div class="flex flex-col gap-2">
            <div
              class="flex items-center gap-4"
              v-for="photo in photos"
              :key="photo.id"
            >
              <el-image :src="photo.src" class="h-[1.875rem] w-[1.875rem]" />
              <h1 class="text-[1.375rem]">{{ photo.title }}</h1>
            </div>
          </div>
          <div class="flex items-center">
            <el-image
              src="/src/assets/googleplay_pic.png"
              class="w-[15rem] cursor-pointer googleplaylogo--HomePage"
            /><el-image
              src="/src/assets/appstore_pic.png"
              class="w-[13.2rem] cursor-pointer appstorelogo--HomePage"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="container mx-auto" id="ContactUs">
      <h1
        class="text-[3.5rem] pt-36 flex justify-center leading-none text-center third-title--HomePage"
      >
        Have Question in Mind?<br />
        Let us help you
      </h1>
      <div class="mx-20 mt-20 fourth-div--HomePage">
        <el-form ref="ruleFormRef" :model="ruleForm" :rules="rules">
          <div class="mx-20 flex flex-col gap-2 fifth-div--HomePage">
            <div class="grid grid-cols-2 gap-8 form--HomePage pb-2">
              <el-form-item prop="Phone">
                <el-input
                  placeholder="Your phone number"
                  type="text"
                  class="pb-3"
                  v-model="ruleForm.Phone"
                />
              </el-form-item>
              <el-form-item prop="Question"
                ><el-input
                  placeholder="Question type"
                  class="pb-3"
                  type="email"
                  v-model="ruleForm.Question"
              /></el-form-item>
            </div>
            <div class="flex flex-col gap-2 second-form--HomePage pb-36">
              <el-form-item prop="TextArea">
                <el-input
                  placeholder="Enter your question"
                  resize="none"
                  type="textarea"
                  rows="5"
                  maxlength="150"
                  show-word-limit
                  v-model="ruleForm.TextArea"
                  class="pb-3"
              /></el-form-item>
              <el-form-item class="btn-form--HomePage pt-2"
                ><el-button @click="SubmitMessage(ruleFormRef)">Send</el-button>
              </el-form-item>
            </div>
          </div>
        </el-form>
      </div>
    </div>
    <div class="scroll-icon--HomePage" id="iconUp">
      <el-icon :size="30" @click="scrollUpFunction()"
        ><ArrowUpBold class="iconUp--HomePage"
      /></el-icon>
    </div>
  </div>
</template>
