
import type { watch } from 'vue';
<template>
    <div>
        <h2>Person</h2>
        <p>姓名：{{ person.name }}</p>
        <p>年龄：{{ person.age }}</p>
        <p>车子：{{ person.car.brand }}</p>
        <p>价格：{{ person.car.price }}</p>
        <button @click="changeName">修改姓名</button>
        <button @click="changeAge">修改年龄</button>
        <button @click="changeBrand">修改品牌</button>
        <button @click="changePrice">修改价格</button>
    </div>
</template>

<script lang="ts" setup>
import { reactive, watch } from 'vue'
// 数据

let person = reactive({
    name: '张三',
    age: 18,
    car: {
        brand: '宝马',
        price: 1000000
    }
})

// 方法
function changeName() {
    person.name += '~'
}
function changeAge() {
    person.age += 1
}
function changeBrand() {
    person.car.brand = '奔驰'
}
function changePrice() {
    person.car.price += 100000
}

watch(person.car, (newVal, oldVal) => {
    console.log('person changed', newVal, oldVal)
})

</script>
