<script setup>
import { ref } from 'vue';

//ตัวแปร
const travel = ref("");
const money = ref(0);

//const travelList=ref(['ท่าช้าง','GoodViews','RiverSide','WarmUp','ตะวันแดง'])
const travelList=ref([
  {name:'ท่าช้าง', price:80 , size: {s:80, m: 150, l:120}, img:"https://www.tripgether.com/wp-content/uploads/tripgetter/thachang_3-1.jpg"},
  {name:'GoodViews', price:120 , size: {s:120, m: 180, l:250}, img:"https://www.tripgether.com/wp-content/uploads/tripgetter/goodview_1.jpg"},
  {name:'RiverSide', price:150 , size: {s:150, m: 190, l:300}, img:"https://www.tripgether.com/wp-content/uploads/tripgetter/riverside_2.jpg"},
  {name:'WarmUp', price:100 , size: {s:100, m: 200, l:500}, img:"https://www.tripgether.com/wp-content/uploads/tripgetter/warmupcafe_1.jpg"},
  {name:'ตะวันแดง', price:90 , size: {s:90, m: 250, l:700}, img:"https://img-prod.api-onscene.com/cdn-cgi/image/format=auto,width=640/https://sls-prod.api-onscene.com/partner_files/trueidintrend/21246/CC697BDB-184E-48B4-9CD1-A85019FE3B35.jpeg"},
  
]);
//เก็บข้อมูลการจองร้าน
const bookingList = ref([
  //"GoodView", "ตะวันแดง"ม............
])


//function
function booking(name){
  //name --> +. bookingList[ ]
  bookingList.value.push(name)
}
</script>
<template>
  <div class="header"><u><font color =""><b><h1>cafe</h1></b></font></u></div>
  <div class="p-3 m-0 border-0 bd-example m-0 border-0">
    <div class="text-center">
      <div class="row row-col-1 row-cols-md-3 g-4">
        <div class="col" v-for="(i,index) in travelList" :key="index">
          <div class="card" style="width: 18rem;">
            <img :src="i.img" class="card-img-top" alt="..." />
            <div class="card-body">
              <h5 class="card-title">{{i.name}}</h5>
              <a class="btn btn-primary" @click="booking(i.name)">จองโต๊ะ</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">ชื่อร้าน</th>
      <th scope="col">price</th>
      <th scope="col">size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>ท่าช้าง</td>
      <td>80</td>
      <td>s:80, m: 150, l:120</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>GoodViews</td>
      <td>120</td>
      <td>s:120, m: 180, l:250</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>RiverSide</td>
      <td>150</td>
      <td>s:150, m: 190, l:300</td>
    </tr>
    <tr>
      <th scope="row">4</th>
      <td>WarmUp</td>
      <td>100</td>
      <td>s:100, m: 200, l:500</td>
    </tr>
    <tr>
      <th scope="row">5</th>
      <td>ตะวันแดง</td>
      <td>90</td>
      <td>s:90, m: 250, l:700</td>
    </tr>
  </tbody>
</table>

  <table class="table table-striped" v-if="bookingList.length > 0">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">รายชื่อร้านที่จอง</th>
      <th scope="col">จำนวนโต๊ะ</th>
      <th scope="col">ชื่อคนจอง</th>
      <th scope="col">เบอร์โทร</th>
      <th scope="col">วันที่</th>
      <th scope="col">เวลา</th>
    </tr>
  </thead>
  <tbody>
    
    <tr v-for="(item, index) in bookingList " key="index">
      <th scope="row">{{ index+1 }}</th>
      <td>{{ item }}</td>
      <td><input type="number"></td>
      <td><input type="text"></td>
      <td><input type="text"></td>
      <td><input type="date"></td>
      <td><input type="time"></td>


    </tr>

  </tbody>
</table>
</template>