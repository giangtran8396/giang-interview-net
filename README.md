# 📘 Table of Contents

- [C#](#-C#)
    - [1. Generic](#1-generic)
    - [2. Delegate](#1-delegate)
    - [3. Event](#1-event)

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