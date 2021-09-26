<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />

    <Form @submit="onSubmit" v-slot="{ errors }">
      {{ errors }}
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <Field
          id="email"
          name="email"
          type="email"
          class="form-control"
          placeholder="請輸入 Email"
          rules="email|required"
          :class="{ 'is-invalid': errors['email'] }"
          v-model="user.email"
        ></Field>
        <ErrorMessage name="email" class="invalid-feedback"></ErrorMessage>
      </div>

      <div class="mb-3">
        <label for="name" class="form-label">姓名</label>
        <Field
          id="name"
          name="姓名"
          type="text"
          class="form-control"
          placeholder="請輸入姓名"
          v-model="user.name"
          :class="{ 'is-invalid': errors['姓名'] }"
          rules="required"
        ></Field>
        <ErrorMessage name="姓名" class="invalid-feedback"></ErrorMessage>
      </div>

      <div class="mb-3">
        <label for="phone" class="form-label">電話</label>
        <Field
          id="phone"
          name="電話"
          type="text"
          class="form-control"
          placeholder="請輸入電話"
          :rules="isPhone"
          v-model="phone"
          :class="{ 'is-invalid': errors['電話'] }"
        ></Field>
        <ErrorMessage name="電話" class="invalid-feedback"></ErrorMessage>
      </div>

      <div class="mb-3">
        <label for="region" class="form-label">地區</label>
        <select id="region" name="地區" class="form-control">
          <option value="">請選擇地區</option>
          <option value="台北市">台北市</option>
          <option value="高雄市">高雄市</option>
        </select>
        <span class="invalid-feedback"></span>
      </div>

      <div class="mb-3">
        <label for="address" class="form-label">地址</label>
        <input
          id="address"
          name="地址"
          type="text"
          class="form-control"
          v-model="user.address"
          placeholder="請輸入地址"
        />
        <span class="invalid-feedback"></span>
      </div>

      <button class="btn btn-primary" type="submit">Submit</button>
    </Form>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      user: {
        email: "",
        name: "",
        address: "",
        phone: "",
      },
    };
  },
  methods: {
    onSubmit() {
      console.log(this.user);
    },
    isPhone(value) {
      const phoneNumber = /^(09)[0-9]{8}$/;
      return phoneNumber.test(value) ? true : "需要正確的電話號碼";
    },
  },
  created() {
    console.log(this);
  },
};
</script>
