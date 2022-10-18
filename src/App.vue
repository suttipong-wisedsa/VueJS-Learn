<template>
  <section>
    ป้อนชื่อเล่น :<input type="text" @input="setNickname" />
    <h1>ชื่อเล่น:{{ nickName }}</h1>
    <!--Form-->
    <form @submit="submitForm">
      <label>ป้อนชื่อเล่น</label>
      <input type="text" @change="setNickname" />
      <button type="submit">บันทึก</button>
    </form>
    <h1>ชื่อ:{{ firstname }}นามสกุล:{{ lastname }}</h1>
    <h1>ชื่อ:{{ getFullName() }}</h1>
    <p>:อายุ{{ age + age }}</p>
    <p v-html="address"></p>
    <!--ทำให้เบาเซอร์เข้าใจ html-->
    <img v-bind:src="picture" width="80" height="80" ref="imageEl" />
    <!--ผูกตัวแปรกับ attibult(src)ที่ทำงานใน html-->
    <!--ref ใช้อ้างอิงโครงสร้างใน tag ไปใช้ใน script-->
    <!--V-show ไว้แสดง element-->
    <button @click="toggle">Toggle{{ isActive }}</button>
    <!--เขียนแบบลดรูป(ternary operater)-->
    <button @click="toggle">{{ isActive ? "แสดง" : "ซ่อน" }}</button>
    <div v-show="isActive">
      <!--v-if&&v-else-->
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <!--Loop Array คล้ายๆ Map()-->
        <ul>
          <li v-for="(item, index) in hobby" :key="index">
            {{ index + 1 }}.{{ item }}
          </li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน</p>
      <!--Loop array object-->
      <ul>
        <li v-for="(item, key) in general" :key="key">
          {{ key }}.{{ item }}
          <!--{key:value(item)}-->
        </li>
      </ul>
    </div>
    <!--Event-->
    <button @click="showData">คลิกปุ่ม</button>
    <button @click="increment(10)">เพิ่ม 10</button>
    <!--Event Argument-->
    <button @click.ctrl="decrement">ลด</button>
    <!--Event Modifier(กด CTRL + เมาส์)-->
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    // data() ใช้ return ข้อมูล ในรูป Object ไปใช้ใน template
    return {
      firstname: "บอส",
      lastname: "ครับ",
      age: 11,
      address: "<h1>ภูเก็ต</h1>", //ส่งเป็นhtml
      a: String,
      b: String,
      nickName: "",
      picture: "https://cdn-icons-png.flaticon.com/512/276/276130.png",
      hobby: ["ถ่ายรูป", "ปั่นจักรยาน", "ฟังเพลง", "เล่นเกม", "ทำอารหาร"],
      general: { gender: "ชาย", weight: 70, height: 170, status: false },
      isActive: false,
    };
  },
  methods: {
    //เขียน fucntion ในนี้
    getName() {
      return (this.b = this.lastname);
    },
    getFullName() {
      this.a = this.firstname + this.getName(); //this. เรียกใช้ methods
      return this.a; //ใน methods ต้องใช้ this. ในการดึงข้อมูลตัวแปร
    },
    showData() {
      alert(this.firstname);
    },
    increment(value) {
      this.age += value;
    },
    decrement() {
      this.age--;
    },
    setNickname(e) {
      this.nickName = e.target.value;
    },
    submitForm(e) {
      e.preventDefault();
      alert("บันทึก");
      console.log(this.$refs.imageEl);
    },
    toggle() {
      this.isActive = !this.isActive;
    },
  },
};
</script>

<style>
button {
  display: block;
}
</style>
