<template>
<ion-page>
  <section>
    <img :src="picture" :width="size" :height="size" ref="imageEl" /><br />
    <h1>ชื่อ-นามสกุล : {{ getFullName }}</h1>
    <h1>อายุ : {{ age }} ปี</h1>
    
    <h1>อาชีพ : {{getDepartment}}</h1>
    
    <button @click="toggleVisible">{{ isVisible ? "ซ่อน" : "แสดง"}}รายละเอียด</button>
    <article v-show="isVisible">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p>Social : <a :href="social" target="_blank">Facebook</a></p>
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก :</p>
        <ul>
          <li v-for="(item, index) in hobby" :key="index">{{ item }}</li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน :</p>
      <ul>
        <li v-for="(item, key) in general" :key="key">{{ item }}</li>
      </ul>
    </article>
  </section>
  </ion-page>
</template>



<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "จักรกฤษ",
      lastName: "สุขาจารย์",
      age: 20,
      address: "<i>7/2 หมู่ 9 ต.โคกสลุด อ.บางกระทุ่ม จ.พิษณุโลก</i>",
      picture:"https://scontent.fphs2-1.fna.fbcdn.net/v/t1.6435-9/118098771_1682404401948515_1388789842709794893_n.jpg?_nc_cat=101&ccb=1-5&_nc_sid=09cbfe&_nc_eui2=AeFvb2VjvRUnnk4o0K-f7lfslHLw2pjnOliUcvDamOc6WOKVQW0pdYLbZ8xf_imm56RpXqWSkGL7Z8zDsIh18I1l&_nc_ohc=Z0fykmd5nq8AX8SlTdF&_nc_ht=scontent.fphs2-1.fna&oh=00_AT-2nss0_C5-tnIoWn297VB2quEp3gTRbF2kARcQ0tohtg&oe=623BEAB1",
      size: 150,
      social: "https://www.facebook.com/profile.php?id=100005369141576",
      hobby: [
        "ดูหนัง",
        "เล่นเกม",
        "เลี้ยงสัตว์",
        "ช่วยงานบ้าน",
        "อ่านมังงะ",
        
      ],
      general: { gender: "เพศ : ชาย", weight: "น้ำหนัก : 52", height: "ส่วนสูง : 167",  },
      isVisible:false,
      
    };
  },
  methods: {
    toggleVisible(){
        this.isVisible = !this.isVisible
    },
    addSalary(value){
        this.salary+=value
    }
  },
  computed:{
    getFullName() {
        return `${this.firstName}  ${this.lastName}`;
    },
    getIncome(){
        return this.salary * 12;
    },
    getDepartment(){
        return this.salary >=35000 ? "Project manager" : "นักศึกษา"
    }
  },
  
  
};
</script>

<style></style>
