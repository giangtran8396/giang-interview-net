# 📘 Table of Contents

- [C#](#-c)
    - [1. Generic](#1-generic)
    - [2. Delegate](#2-delegate)
    - [3. Event](#3-event)
    - [4. Exception Handling](#4-exception-handling)
    - [5. Lambda Expressions](#5-lambda-expressions)
    - [6. Thread](#6-thread)
    - [7. Asynchronous](#7-asynchronous)
    - [8. Task & Threading & Concurrency](#8-task-&-threading-&-concurrency)
    - [9. OOP](#9-oop)
    - [10. Class, Object, Struct, Interface](#10-class-object-struct-interface)
    - [11. Dispose, Destructor, Finalize](#11-dispose-destructor-finalize)
    - [12. Copy and Clone](#12-copy-and-clone)
    - [13. Abstract and Interface](#13-abstract-and-interface)
    - [14. Var and Dynamic](#14-var-and-dynamic)
    - [15. Coding convention](#15-coding-convention)
    - [16. is and as keyword](#16-is-and-as-keyword)
    - [17. C# 8,9](#17-c-89)
    - [18. When asynchonous deadlock](#18-when-asynchonous-deadlock)
    - [19. Vitural and abstract](#19-vitural-and-abstract)
- [.NET](#net)
    - [1. IEnumerable vs ICollection vs IList vs IQueryable](#1-ienumerable-vs-icollection-vs-ilist-vs-iqueryable)
    - [2. Net Standard](#2-net-standard)
    - [3. Model Validation](#3-model-validation)
    - [4. Why using yield](#4-why-using-yield)
    - [5. HttpApplication, Session, ViewSate and HttpContext](#HttpApplication-Session-ViewSate-and-HttpContext)
- [.NET Core](#net-core)
    - [1. Life cycle](#1-life-cycle)
    - [2. Startup](#1-life-cycle)
    - [3. LifeTime](#3-lifetime)
    - [4. Dependency](#4-dependency)
    - [5. Middleware](#5-middleware)
    - [6. Filter](#6-filter)
    - [7. Logging](#7-logging)
    - [8. Configuration](#8-configuration)
    - [9. Error Handling](#8-error-handling)
    - [10. Routing](#10-routing)
    - [11. Attribute](#11-Attribute)
    - [12. iHostBuilder](#12-iHostBuilder)
    - [13. .Net Core vs .Net Framework](#13-net-core-vs-net-framework)
    - [14. ActionResult and JsonResult](#8-ActionResult-and-JsonResult)
- [Entity framework](#entity-framework)
    - [1. How many type](#1-how-many-type)
    - [2. LazyLoading, EagerLoading, Explicit Loading](#2-lazyloading-eagerloading-explicit-loading)
    - [3. State in Entity framework ](#3-state-in-entity-framework)
    - [4. IEnumerable vs IQueryable](#4-ienumerable-vs-iqueryable)
    - [5. SingleOrDefault vs FirstOrDefault](#5-singleordefault-vs-firstordefault)
    - [6. Store Procedure vs View vs Function vs Query](#6-store-procedure-vs-view-vs-function-vs-query)
    - [7. Trigger](#7-trigger)
- [Web security](#web-security)
    - [1. OWASP10](#1-OWASP10)
- [CI/CD](#cicd)
- [Design Partten](#design-partten)
    - [1. Clean Architechture](#clean-architechture)
    - [2. DDD](#2-ddd)
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

### 6. Thread
- Tạo một luồng xử lý cho một tác vụ. có thể tạo nhiều luồng
- C# có 2 luồng chính Main Thread (luồng chính) và UI thread (luồng ui)
- Sử dụng thread để thực hiện đa luồng
- ```
    Thread myThread = new Thread(funtion)
  ```

### 7. Asynchronous
- Xuất hiện từ .NET framework 4.5
- Dùng để thực hiện tạc vụ một cách bất đồng bộ xen kẻ nhau
- Cú pháp `async` và `await` and trả về `Task`
- Tên hậu tố của phương thức phải có chữ `Async`
- Cú pháp `await` sẽ chờ đến khi task đó hoàn thành
- `Task` sẽ tạo ra 1 luồng riêng để chạy
- `Task.Result` cũng sẽ block đoạn lệnh và chờ tới khi nó thực hiện xong mới chạy các tác vụ tiếp theo

  ```
    static async Task Main(string[] args)
    {
        Foo foo = await FooAsync(2);
        Bar bar = await BarAsync(2);
    }
  ```
- Để chạy bất đồng bộ
    ```
    static async Task Main(string[] args)
    {
        Task<Foo> fooTask = FooAsync(2);
        Task<Bar> barTask = BarAsync(2);
        var foo = await fooTask;
        var bar = await barTask;
    }
    ```

### 8. Task & Threading & Concurrency
- Multithread: nhiều thread sẽ được chạy cùng một lúc mỗi thread sẽ đảm nhận 1 tác vụ
- Asynchronous: một thread thực hiện nhiều tác vụ xen kẻ nhau
- Concurrency: Thực hiện nhiều `request` cùng một lúc.

Task | Thread
--- | ---
Task có thể trả về result | Thread không trả về kết quả
Task hổ trợ cancellation Token | Thread thì không
Task can have có thể thực hiện nhiều tác vụ | mỗi Thread sẽ thực hiện một tác vụ trong cùng thời điểm
- Task dễ dàng triển khai với cú pháp `async` và `await`

[Read More](https://codewala.net/2015/07/29/concurrency-vs-multi-threading-vs-asynchronous-programming-explained/)
### 9. OOP
- Abstract
- Inheritance: tái sử dụng code or function or lib
- Encapsulation
- Polymorphism: mục đích: Một hành động có thể xảy ra theo nhiều cách khác nhau.

### 10. Class, Object, Struct, Interface
- Class: là một cấu trúc dử liệu dc người dùng định nghĩa các method, thuộc tính. (reference type)
- Object: là một trường hợp củ thể của class, class ko chiếm bộ nhớ, object thì chiếm bộ nhớ khi khởi tạo 1 class - đó là 1 object.
- Struct: là một cấu trúc dữ liệu (value type)
- Interface: chứa các function or method được quy định trước need to implement.


### 11. Dispose, Destructor, Finalize
- Destructor:  sẻ chuyển thành Finalize khi compile,
- Finalize:  Được gọi bởi .net runtime và chúng ta ko biết khi nào sẻ dc gọi nhưng chắc chắn sẻ dc gọi.
- Dispose: giải phóng vùng nhớ khi dc gọi. sử dụng keyword “Using” to call dispose.

### 12. Copy and Clone
- Clone sẻ copy cấu trúc của object
- Copy sẻ copy cấu trúc và values của object.

### 13. Abstract and Interface
- Abstract and Interface không thể khởi tạo đối tượng bên trong
- Dùng để khai báo phương thức
- Đùng để các class kế thừa
- Abstract
    - Có thể khai báo field
    - Chỉ được kế thừa 1 abstract class
    - có thể implement hoặc không
- Interface
    - có thể implements nhiều interface
    - không thể định nghĩa bên trong hàm

### 14. Var and Dynamic
- var
    - Biến phải được khởi tạo cùng với giá trị
    - Compiler xác định kiểu trả về
    ```
    var a = 6;
    ```
- Dynamic
    - Biến không cần khởi tọa
    - Runtime xác định kiểu trả về
    ```
    dynamic a;
    a = 6;
    a = "abc";
    ```

### 15. Coding convention
- Sử dụng cách viết hoa khi đặt tên cho class, record, or struct.
    ```
    public class DataService { }
    ```
- Khi đặt tên với Interface thường có chữ `I` đầu tiên
    ```
    public intreface IDataService { }
    ```
[Read more](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)

### 16. is and as keyword
- is: sử dụng để kiểm tra kiểu dữ liệu
- as: sử dụng để ép kiểu dữ liệu

### 17. C# 8,9

[Read more](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-8)

[Read more](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-9)

### 18. When asynchonous deadlock

### 19. Vitural and abstract

## 📘 .NET

### 1. IEnumerable vs ICollection vs IList vs IQueryable
- IEnumerable:
    - Namespace: System.Collections
    - không thể add, remove, edit, count
    - bạn cân phải iterate qua các phần tử
    - hỗ trợ filter thông qua mệnh đề clause
- ICollection:
    - Namespace: System.Collections
    - extends từ IEnumerable
    - có thể add, remove, edit, count
- IList:
    - Namespace: System.Collections.Generic
    - extends từ ICollection, IEnumerable
    - hỗ trợ hàm index, IndexOf, Insert, RemoveAt

- IQueryable:
    - Namespace: System.Linq
    - extends từ IEnumerable
    - dùng để build câu query truy vấn SQL

- IDictionary:
    - System.Collections.Generic
    - Chứa dữ liệu theo dạng Key Value
    - Có các hàm Add,ContainsKey,Remove

### 2. Net Standard

### 3. Model Validation

### 4. Why using yield

### 5. HttpApplication, Session, ViewSate and HttpContext

## 📘 .NET Core

### 1. Life cycle

### 2. Startup

### 3. LifeTime

### 4. Dependency

### 5. Middleware

### 6. Filter

### 7. Logging

### 8. Configuration

### 9. Error Handling

### 10. Routing

### 11. Attribute

### 12. iHostBuilder

### 13. .Net Core vs .Net Framework


### 14. ActionResult and JsonResult

## 📘 .Entity framework

### 1. How many type

### 2. LazyLoading, EagerLoading, Explicit Loading

### 3. State in Entity framework

### 4. IEnumerable vs IQueryable

### 5. SingleOrDefault vs FirstOrDefault

### 6. Store Procedure vs View vs Function vs Query

### 7. Trigger

## 📘 Web security

### 1. OWASP10

## 📘 CI/CD

## 📘 Design Partten

### 1. Clean Architechture

### 2. DDD









