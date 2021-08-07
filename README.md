# 📘 Table of Contents

- [C#](#-C#)
    - [1. Generic](#1-generic)
    - [2. Delegate](#2-delegate)
    - [3. Event](#3-event)
    - [4. Exception Handling](#4-exception-handling)
    - [5. Lambda Expressions](#5-lambda-expressions)

## 📘 C#

### 1. Generic

- C# allow define generic class, interface, abstract class, fields, methods, static methods, property, event, delegates without the specific data type
- using for `desgin partten` like `Repository Parttern`
- using write helper common methods

    ```
    class DataStore<T>
    {
        public T Data { get; set; }
    }
    ```
### 2. Delegate
- `Delegate` là một `biến kiểu tham chiếu`(references) chứa tham chiếu tới một phương thức.
- Phương thức nhận vào phải có `cùng tham` số và `kiểu trả về`
- `Delegate` thường được dùng để triển khai các phương thức hoặc sự kiện call-back
- `Delegate` có thể thay đổi runtime
- cú pháp
    - `delegate` <kiểu trả về> <tên delegate> (<danh sách tha số nếu có>);
    -  ```
        delegate int MyDelegate(string s);
        ```
- `Delegate` có thể multicashing
    - ```
        MyDelegate convertToInt = new MyDelegate(ConvertStringToInt);
        MyDelegate showString = new MyDelegate(ShowString);
        MyDelegate multicast = convertToInt + showString;
      ```
    > Mục đích chỉ để gọi tuần tự chứ `không cộng giá trị lại với nhau`

[Read more](https://www.howkteam.vn/course/khoa-hoc-lap-trinh-c-nang-cao/delegate-trong-c-4040)

### 3. Event
- `Event` là `Delegate` với mục đích để cho lớp khác hoặc đối tượng cha của đối tượng hiện tại ủy thác(định nghĩa) hàm vào trong đó.
- Mục đích chính của chuyện này là để thông báo lên cho đối tượng cha biết mà xử lý.
    - ```
        event <Kiểu delegate> <tên event>;
      ```
- `Event Chuẩn .NET`
    - `EventHandler`
    - Có kiểu trả về là void
    - `Delegate` có hai tham số, tham số thứ nhất có kiểu dữ liệu là `object`, tham số thứ hai có kiểu `EventArgs`. `object` chính là đối tượng phát sinh sự kiện, `EventArgs` chính là class giữ thông tin mà đối tượng gửi kèm trong quá trình phát sinh sự kiện.

[Read more](https://www.howkteam.vn/course/khoa-hoc-lap-trinh-c-nang-cao/event-chuan-net-trong-c-4042)

### 4. Exception Handling
- C# support exception handling with try catch finally
  - `try` một khối được dùng để viết mã
  - `catch` khi try có lỗi sẽ được catch bắt
  - `finally` sau khi try xong khối try, catch finally sẽ được gọi, `finally luôn luôn được gọi cuối cùng cho dù catch có xảy ra hay không`
  - `throw` được dùng để ném lỗi khi chúng ta muốn handle lỗi
  - ```
    try {

    } catch {

    }
    finally {

    }
    ```
 - C# hỗ trợ một số thư viện lỗi
    - System.IndexOutOfRangeException
    - System.ArrayTypeMismatchException
    - System.NullReferenceException
    - System.OutOfMemoryException
    - System.InvalidCastException
- Có thể custom exception bằng cách kế thừa Exception

### 5. Lambda Expressions
- Là một annonymous function được sử dụng bằng dấu `=>`
- Dùng để tạo cây biểu thức (expression condition query)
- Dùng lambda expression để viết code ngắn hơn với những function không cần đặt tên. hoặc dùng để trả về giá trị trong một function chỉ có dòng duy nhất là `return`
- giúp code ngắn dễ hiểu về dễ đọc hơn

- ```
  (x, y) => x == y
  ```