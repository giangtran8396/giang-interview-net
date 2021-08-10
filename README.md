# 📘 Table of Contents

- [C#](#-c)
    - [1. Generic](#1-generic)
    - [2. Delegate](#2-delegate)
    - [3. Event](#3-event)
    - [4. Exception Handling](#4-exception-handling)
    - [5. Lambda Expressions](#5-lambda-expressions)
    - [6. Thread](#6-thread)
    - [7. Asynchronous](#7-asynchronous)
    - [8. Task & Threading & Concurrency](#8-task--threading--concurrency)
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
- [.NET](#-net)
    - [1. IEnumerable vs ICollection vs IList vs IQueryable](#1-ienumerable-vs-icollection-vs-ilist-vs-iqueryable)
    - [2. Net Standard](#2-net-standard)
    - [3. Model Validation](#3-model-validation)
    - [4. Why using yield](#4-why-using-yield)
    - [5. HttpApplication, Session, ViewSate and HttpContext](#5-httpapplication-session-viewsate-and-httpcontext)
- [.NET Core](#-net-core)
    - [1. Life cycle](#1-life-cycle)
    - [2. Startup](#2-startup)
    - [3. LifeTime](#3-lifetime)
    - [4. Dependency](#4-dependency)
    - [5. Middleware](#5-middleware)
    - [6. Filter](#6-filter)
    - [7. Logging](#7-logging)
    - [8. Configuration](#8-configuration)
    - [9. Error Handling](#9-error-handling)
    - [10. Routing](#10-routing)
    - [11. Attribute](#11-attribute)
    - [12. iHostBuilder](#12-ihostbuilder)
    - [13. .Net Core vs .Net Framework](#13-net-core-vs-net-framework)
    - [14. ActionResult and JsonResult](#14-actionresult-and-jsonresult)
- [Entity framework](#entity-framework)
    - [1. How many type](#1-how-many-type)
    - [2. LazyLoading, EagerLoading, Explicit Loading](#2-lazyloading-eagerloading-explicit-loading)
    - [3. State in Entity framework ](#3-state-in-entity-framework)
    - [4. IEnumerable vs IQueryable](#4-ienumerable-vs-iqueryable)
    - [5. SingleOrDefault vs FirstOrDefault](#5-singleordefault-vs-firstordefault)
    - [6. Store Procedure vs View vs Function vs Query](#6-store-procedure-vs-view-vs-function-vs-query)
    - [7. Trigger](#7-trigger)
- [Web security](#-web-security)
    - [1. OWASP10](#1-owasp10)
- [CI/CD](#-cicd)
- [Design Partten](#-design-partten)
    - [1. Clean Architechture](#1-clean-architechture)
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

```
// My "library" method.
public static async Task<JObject> GetJsonAsync(Uri uri)
{
  // (real-world code shouldn't use HttpClient in a using block; this is just example code)
  using (var client = new HttpClient())
  {
    var jsonString = await client.GetStringAsync(uri);
    return JObject.Parse(jsonString);
  }
}

// My "top-level" method.
public class MyController : ApiController
{
  public string Get()
  {
    var jsonTask = GetJsonAsync(...);
    return jsonTask.Result.ToString();
  }
}
```
1. The top-level method calls `GetJsonAsync`
2. `GetJsonAsync` starts the REST request by calling `HttpClient.GetStringAsync`
3. `GetStringAsync` returns an uncompleted Task, indicating the REST request is not complete
4. `GetJsonAsync` awaits the Task returned by `GetStringAsync`. The context is captured and will be used to continue running the `GetJsonAsync` method later. `GetJsonAsync` returns an uncompleted Task, indicating that the `GetJsonAsync` method is not complete.
5. The top-level method synchronously blocks on the Task returned by `GetJsonAsync`. This `blocks the context thread`.
6.  the REST request will complete. This completes the Task that was returned by `GetStringAsync`.
7. The continuation for `GetJsonAsync` is now ready to run, and it waits for the context to be available so it can execute in the context.
8. Deadlock. The top-level method is blocking the context thread, waiting for `GetJsonAsync` to complete, and `GetJsonAsync` is waiting for the context to be free so it can complete.


[Read more](https://blog.stephencleary.com/2012/07/dont-block-on-async-code.html)

### 19. Vitural and abstract
- Vitural methods `có thể implement` trước và lớp kế thừa có thể quyết định `override hoặc không` 
- Abstract methods `không thể implement` và bắt buộc lớp kế thừa `phải override` lại phương thức đó
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
- .Net standard là interface để thống nhất các thư viện implementation cụ thể cần xây dựng. giúp các framework chia sẽ code với nhau

- Sử .Net Standard có thể build thư viện chia sẽ với tất cả các app cho dù chúng đang chạy trên OS nào hoặc là framework nào    

### 3. Model Validation
- Sử dụng DataAnotation trong các property
    - [Required], [StringLength(100)]
    - [StringLength(8, ErrorMessage = "Name length can't be more than 8.")]`
- Sử dụng ModelState để kiểm tra validation
    - ModelState.IsValid
- Trên giao diện sử dụng asp-validation-for="Firstname"
### 4. Why using yield
- Sử dụng yield khi muốn lấy những item tiếp theo mà không cần chờ list completed hoàn toàn
- Nếu không sử dụng yield bắt buộc phải chờ cho list complite mới sử dụng được
- A yield return không thể nằm trong try catch.
- Không sử dụng ref out khi sử dụng yeild
- A yield return có thể nằm trong try finally.
- không thể yield return bên trong annonymous function
- Sử dụng Yield giúp tiết kiệm khi tạo thêm 1 mảng tạm
```
  // Usually Dev use this scenario
        private static List<int> GetListIndex1(List<int> listData, int valueFind)
        {
            List<int> listIdx = new List<int>();// no need create this list when using yield
            for (int ii = 0; ii < listData.Count; ii++)
            {
                if (listData[ii] == valueFind)
                    listIdx.Add(ii);
            }
            return listIdx;
        }
 
        // Use yield
        private static IEnumerable<int> GetListIndex2(List<int> listData, int valueFind)
        {
            for (int ii = 0; ii < listData.Count; ii++)
            {
                if (listData[ii] == valueFind)
                    yield return ii;
            }
        }
```


### 5. HttpApplication, Session, ViewSate and HttpContext
- Tất cả dung để lưu trử của web application.
- HttpApplication: có tác dụng trong toàn bộ quá trình thực thi của web application.
- Session: có tác dụng trong 1 lần ghé thăm của 1 user, và sẻ hết khi timeout.
- ViewState: có tác dụng trên view.
- HttpContext: có tác dụng trên 1 request, handler everything relate to request. Ex: header, cookie of request, user agent, accepted language …
## 📘 .NET Core

- .Net core là cross platform. Tức là chạy dc trên 2 nhân Window va Linux.
- .Net core là Open soure cự kỳ quan trọng ve license khi làm product.
- .Net core cải thiện performance so vs .Net framework
- .Net core phù hợp cho dự án cần scale up, thích hợp microservice.

### 1. Life cycle

- Bắt đầu từ  Program (Main) -> (Start Up class -> ConfigureService() -> Configure() )
- ConfigureService -> add DbContext, add Identity, Add Mvc, Add DI
- Configure ->   middleware components are initialized, this area is initial Middleware. (key work: Use*Action* Middleware, Run, Map) Ex: UseExceptionHandler, UseStaticFiles, UseIdentity, UseMVC

### 2. Startup

- thông thường dùng để init, loadconfig của app 
- Startup class được chỉ định trong file Program.cs của ứng dụng khi app bắt đầu chạy
- Có thể đưa vào contrucstor của start up các types như sau
    - IWebHostEnvironment
    - IHostEnvironment
    - IConfiguration
- có 2 method bên trong ConfigureServices, Configure
- ConfigureServices method dùng để cấu hình các service
    - các hàm sử dụng ConfigureServices thường có dạng IServiceCollection và tên bắt dầu bằng Add{extension}
    - AddDbContext, AddDefaultIdentity...
- Configure method dùng để cấu hình app, pipeline, middleware 
    - sử dụng những extension bắt đầu bằng Use
    - UseHttpsRedirection, UseStaticFiles,
, UseRouting

### 3. LifeTime

- AddSingleton: Một thể hiện duy nhất được tạo và chia sẻ xuyên suốt thời gian chạy của ứng dụng.
- AddScoped: Trong cùng một request, object sẽ được chia sẽ lẫn nhau. thường sữ dụng cho DbContext
- AddTransient: luôn luôn trả về object mới cho mỗi request

### 4. Dependency
- .NET Core support Dependency để thực hiện kỹ thuật IOC (Inversion Of Control)
- Các class không giao tiếp trực tiếp với nhau mà thông qua Interfaces
- Giảm việc phụ thuộc giữa các class
- .NET Core hỗ trợ việc đăng ký các service và Interfaces và thêm vào IServiceCollection
- các Service sẽ được inject vào contructor của class muốn sữ dụng thông qua Interfaces
- IOC là nguyên lý còn DI là cách đẻ thực hiện IOC
### 5. Middleware

- Là một thành phần trung gian cho phép xử lý request và response cho mỗi HTTP request. trước khi vào code của chúng ta
- Middleware là phương thức mở rộng của `IApplicationBuilder`
- Được thêm vào StartUp -> Configure
- Gồm 3 thành phần: Use, Run, Map
- Use
    - Dùng để xâu chuổi nhiều middleware
    - `Next` parameter đại diện cho một middleware tiếp theo
    ```
     app.Use(async (context, next) =>
        {
            await next();
        });
    ```
- Run
    - Thường được đặt ở cuối cùng
    - Không có tham số `next`
    - Nếu có một `Use` hoặc `Run` khác sau `Run` nó sẽ không chạy
    ```
    app.Run(async context =>
        {
            await context.Response.WriteAsync("Hello from 2nd delegate.");
        });
    ```
- Map
    - Được sử dụng khi muốn kiếm tra với path
    - Nếu request start with path thì branch đó được thực hiện
    ```
    app.Map("/map1", HandleMapTest1);
    ```
- NET Core hỗ trợ người dùng viết custom middleware
    - Phương thức Contructor phải có RequestDelegate
    - Một phương thức tên là `Invoke` hoặc `InvokeAsync`
        - Trả về một Task
        - nhận vào một HttpContext
    ```
    public class CustomMiddleware
    {
        private readonly RequestDelegate _next;

        public CustomMiddleware(RequestDelegate next)
        {
            _next = next;
        }

        public async Task Invoke(HttpContext httpContext)
        {
            await _next(httpContext);
        }
    }
    ```
    ```
    using Microsoft.AspNetCore.Builder;
    namespace Custom
    {
        public static class RequestCustomMiddlewareExtensions
        {
            public static IApplicationBuilder UseRequestCustom(
                this IApplicationBuilder builder)
            {
                return builder.UseMiddleware<CustomMiddleware>();
            }
        }
    }
    ```
    ```
    public class Startup
    {
        public void Configure(IApplicationBuilder app)
        {
            app.UseRequestCustom();
        }
    }
    ```
- Một số Middleware cơ bản
    - `UseCors`, `UseAuthentication`, `UseRouting`, `UseStaticFiles`
### 6. Filter
- filter hoạt động với action invocation. filter chạy sau middleware
- Dùng để filter các action, response caching, logging
- Sử dụng bằng Attribute ServiceFilter
- Một số filter thông dụng
    - OnActionExecuting // Do something before the action executes
    - OnActionExecuted // Do something after the action executes.
    - OnResultExecuting // before return response eg: set header
    - OnResultExecuted // after return response eg: write log
    - OnException // Exception Filter
    - IAlwaysRunResultFilter, IAsyncAlwaysRunResultFilter // run for all action result
![image info](./assert/img/filter-pipeline-1.png)
- Filter, Middleware
    - Nếu không cần dùng context thì sử dụng middleware
    - Nếu cần dùng context thì sử dụng filter
![image info](./assert/img/filter-pipeline-2.png)
### 7. Logging

- CreateHostBuilder của IHostBuilder có hỗ trợ phương thức mở rộng ConfigureLogging. Cho phép sử dụng logger
- Logger được config trong file appsettings.{Environment}.json
```
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();//xóa tất cả logger provider trước
            logging.AddConsole();
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

### 8. Configuration

### 9. Error Handling

### 10. Routing

### 11. Attribute

### 12. iHostBuilder
- Được sử dụng trong file Programs để CreateHostBuilder
- và sẽ sử dụng Startup để build web host

### 13. .Net Core vs .Net Framework


### 14. ActionResult and JsonResult

## 📘 Entity framework

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









