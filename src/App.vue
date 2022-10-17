<template>
  <section>
    <h1>ชื่อ:{{firstname}}</h1>
    <h2>{{lastname}}</h2>
    <p>:อายุ{{age+age}}</p>
  </section>
</template>

<script>


export default {
  name: 'App',
  data(){ // data() ใช้ return ข้อมูล ในรูป Object ไปใช้ใน template
    return{
      firstname:"บาส",
      lastname:"ครับ",
      age:11
    }
  }
}
</script>

<style>

</style>
