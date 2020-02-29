---
layout: post
title: "Vẻ đẹp của Swift dưới cái nhìn của 1 amateur iOS developer"
categories: misc
author: "Phat Pham"
meta: "Springfield"
---

Swift là ngôn ngữ lập trình được Apple ra mắt năm 2014 nhằm thay thế Objective C trong việc lập trình hệ sinh thái của hãng. Trải qua hơn 5 năm với hàng loạt cải tiến qua các năm, từ Swift 1 đến hiện tại là Swift 5.1, Swift đã thành một ngôn ngữ lập trình đẹp, hay nói cách khác, tôi sang lập trình các ngôn ngữ khác, tôi đã rất nhớ về nó. Giờ ta cùng đi qua những thứ đã làm nên vẻ đẹp của cô nàng Swift này 😀

## Optional chaining
Optional chaining đóng gói một biến trong Optional, nghĩa là có giá trị hoặc là `nil` (hay null trong các ngôn ngữ khác). Ví dụ về khai báo kiểu `String` với optional
```swift
var optionalName: String? = "Phat"
```
Khi bạn print, console hiện `Optional(Phat)` chứ không phải `Phat`. Và bạn không thể gán một biến optional vào 1 biến không optional
```swift
var optionalName: String? = "Phat"
var name: String = optionalName //Lỗi
```
Vì sao? Vì `optionalName` là biến có thể có giá trị hoặc là `nil`, biến `name` phải là biến có giá trị, ko thể `nil`. Vì thế việc gán cần bước trung gian
```swift
//Cách 1
name = optionalName!
//Cách 2
name = optionalName ?? "Unknown name"
```
Ở cách 1, chương trình sẽ crash nếu biến `optionalName` là nil, còn cách 2 thì chương trình không bao giờ crash, thay vào đó biến `name` có giá trị "Unknown name". Dấu `!` trong câu cú đã nói rằng: Hãy cẩn thận. Vậy tại sao cú pháp dài dòng vậy lại là 1 trong số vẻ đẹp của ngôn ngữ này? Lúc mới tiếp xúc tôi cũng thắc mắc vậy, nhưng sau khi làm một số dự án và nhận ra nó thật tuyệt vời.

Swift là ngôn ngữ lập trình "an toàn", nó đảm bảo khi bạn có 1 biến non-optional, nghĩa là biến đó có giá trị, bạn có thể thoải mái dùng biến đó trong việc khác như cộng chuỗi, split,... mà ko lo chương trình bị crash, điều mà tôi luôn gặp phải khi lập trình `javascript` với `undefined` hay `null`. Swift và Kotlin cùng có đặc điểm này, là các ngôn ngữ hiện đại.

## Enum with associated values
Điểm sáng giá của swift so với các ngôn ngữ khác, Enum kèm giá trị.
```swift
enum Furniture {
  case table(material: String)
  case chair(color: String)
  case desk
}
```
Một biến thuộc kiểu `Furniture` với case `table` hay `chair` phải cung cấp giá trị tương ứng, còn case `desk` thì không. Việc phân loại `enum`, ta có thể làm việc trên các giá trị tương ứng
```swift
var thing: Furniture!
switch thing {
case .chair(let color):
  //Do anything with color variable
  print(color)
default:
  print("Other")
  break
}
```

## Name on parameter
```swift
func add(num1: Int, num2: Int) -> Int {
  return num1 + num2
}
//Usage
print(add(num1: 1, num2: 3))

func fill(_ view: UIView, with color: UIColor) {
  view.backgroundColor = color
}
//Usage
fill(view1, with: .red)
```
Với 2 ví dụ ta thấy gọi hàm trên Swift gần như viết tiếng Anh. 

## Type và Protocol Oriented Programming
Khi lập trình từ C/C++ lên Javasript/Python, tôi đã choáng ngợp bởi sự dễ dàng trong việc sử dụng type. 2 ngôn ngữ đó dùng dynamic type, đúng vậy, bạn có thể gán bất cứ type nào cho 1 biến mà không bị lỗi gì. Sự choáng ngợp đó chỉ xuất hiện với project nhỏ, còn với các project vừa và lớn, nó lại là ác mộng. IDE không gợi ý cho bạn những thứ sẵn có, bạn truyền 1 biến khác type mà hàm mong đợi, chương trình bị crash. Đến lúc tôi cần các ràng buộc rõ ràng hơn.

Swift love type, Xcode IDE cũng gợi ý tường tận từng hàm cho lập trình viên (mặc dù Xcode nặng vãi), khiến việc lập trình trở nên dễ dàng. Từ đó mở rộng ra các kỹ thuật như generic, protocol oriented programming (POP),... Nhắc đến POP thì Swift là ngôn ngữ lập hình hướng POP, từ Swift 2 Apple đã nâng tầm Protocol lên, khiến nó trở nên mạnh mẽ hơn. Một class chỉ có thể kế thừa từ 1 class khác, nhưng có thể kế thừa nhiều protocol để tương thích, giúp lập trình đâu ra đó, có khuôn khổ hơn. 

## Về tác giả
Bài viết của 1 người làm iOS trong hơn 8 tháng, mọi sai sót có thể xảy ra, và tất cả ý trên đều là ý kiến riêng của tôi 😙

Sắp tới web sẽ có nhiều bài viết về hướng dẫn lập trình iOS theo các mức độ từ low đến medium. Mong các bạn đón nhận

[Phat Pham](https://facebook.com/phthphat)