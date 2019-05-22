# โปรแกรมจุดขายสินค้า PoS
ผู้ใช้สามารถป้อนรหัสสินค้าที่ต้องการซื้อ แล้วตัวโปรแกรมจะทำการคำนวณเงินที่ต้องจ่ายทั้งหมดที่หักส่วนลดออกแล้วได้ถูกต้อง

## เงื่อนไข
* รายการสินค้าเบื้องต้นต้องมีอยู่ในระบบ
* การป้อนรหัสสินค้า 1 ครั้ง โปรแกรมจะเพิ่มจำนวนสินค้าที่ต้องการจะซื้อทีละ 1 ชิ้น
* กรณีที่ไม่เจอสินค้ารหัสนั้นๆโปรแกรมจะแจ้งเตือนข้อผิดพลาด
* ผู้ใช้สามารถเพิ่มสินค้าใหม่ได้เอง โดยจะต้องกำหนด `SKU`, `Name` และ `Price` ด้วยเสมอ
* โปรแกรมสามารถสลับโหมดระหว่าง `โหมดคิดเงิน` กับ `โหมดเพิ่มรายการสินค้า` ได้
* สินค้าที่จะซื้อชิ้นที่ 4 ทางร้านจะถือว่าเป็นของแถมเสมอ
* ระบบต้องแสดงราคาก่อนและหลังลด พร้อมกับยอดลดได้
* รูปแบบการแสดงผลในส่วนที่ไม่มีในตัวอย่างให้ไปออกแบบการทำงานเอาเอง

## รายการสินค้าเบื้องต้น
|SKU|Name|Price|
|--|--|--|
|p01|iPad Pro 11-inch|23900|
|p02|Apple Watch Series 4|14400|
|p03|MacBook Pro with Touch Bar|47900|
|p04|Apple TV 4K|8500|
|p05|iPhone XS|39900|
|p06|iPhone XS Max|43900|
|p07|iPhone XR|29900|
|p08|MacBook Air 13-inch|42900|
|p09|Mac Mini 2018|27900|

## ตัวอย่างของโหมดคิดเงิน
ตัวอย่างด้านล่างนี้เป็นการทำงานทีละขั้นตอนตามลำดับ  
> `<<รอรับ input>>` เป็นการรอรับข้อมูลจาก keyboard
```
Products in your cart are
none
---
Subtotal: 0.00 baht
Discount: 0.00 baht
Total due: 0.00 baht
Please input a product key: <<รอรับ input>>
```

ทำการใส่รหัสสินค้า `p01`

```
Products in your cart are
1.iPad Pro 11-inch        23,900.00
---
Subtotal: 23,900.00 baht
Discount: 0.00 baht
Total due: 23,900.00 baht
Please input a product key: <<รอรับ input>>
```

ทำการใส่รหัสสินค้า `p02`

```
Products in your cart are
1.iPad Pro 11-inch        23,900.00
2.Apple Watch Series 4    14,400.00
---
Subtotal: 38,300.00 baht
Discount: 0.00 baht
Total due: 38,300.00 baht
Please input a product key: <<รอรับ input>>
```

ทำการใส่รหัสสินค้า `p02`

```
Products in your cart are
1.iPad Pro 11-inch        23,900.00
2.Apple Watch Series 4    14,400.00
3.Apple Watch Series 4    14,400.00
---
Subtotal: 52,700.00 baht
Discount: 0.00 baht
Total due: 52,700.00 baht
Please input a product key: <<รอรับ input>>
```

ทำการใส่รหัสสินค้า `p02`

```
Products in your cart are
1.iPad Pro 11-inch        23,900.00
2.Apple Watch Series 4    14,400.00
3.Apple Watch Series 4    14,400.00
4.Apple Watch Series 4    14,400.00
---
Subtotal: 67,100.00 baht
Discount: 14,400.00 baht
Total due: 52,700.00 baht
Please input a product key: <<รอรับ input>>
```

> Notes:  
Assume the data is input by console.
