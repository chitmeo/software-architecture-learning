# Object-Oriented Programming (OOP) – Tư duy lập trình hướng đối tượng

## 1. Tại sao chúng ta cần OOP?

Ở bài viết trước, chúng ta đã đề cập đến sự phát triển của các phương pháp lập trình, từ lập trình thủ tục (Procedural Programming) đến lập trình hướng đối tượng (Object-Oriented Programming).

Vấn đề đặt ra là: Tại sao chúng ta cần OOP?

Hãy tưởng tượng bạn đang xây dựng một phần mềm quản lý nhân viên.

Ở phiên bản đầu tiên, hệ thống chỉ cần quản lý một vài nhân viên. Chúng ta có thể sử dụng các biến để lưu thông tin:

```csharp
string employeeName = "John";
int employeeAge = 30;
decimal employeeSalary = 20000000;

void CalculateSalary()
{
    // Calculate salary
}
```

Khi số lượng nhân viên tăng lên, chúng ta có thể sử dụng Array hoặc List để quản lý dữ liệu.

```csharp
string[] employeeNames =
{
    "John",
    "David",
    "Peter"
};

decimal[] employeeSalaries =
{
    20000000,
    25000000,
    30000000
};
```

Cách làm này vẫn có thể giải quyết được bài toán. Tuy nhiên, khi hệ thống phát triển, chúng ta sẽ bắt đầu gặp những vấn đề:

- Thông tin của một nhân viên bị phân tán ở nhiều nơi.
- Các biến dữ liệu không có mối liên kết rõ ràng.
- Các hàm xử lý nghiệp vụ phải nhận rất nhiều tham số.
- Việc thêm một thuộc tính mới có thể khiến chúng ta phải sửa đổi nhiều đoạn code.
- Khó kiểm soát tính hợp lệ của dữ liệu.

Vấn đề thực sự không nằm ở số lượng dòng code, mà nằm ở cách chúng ta tổ chức và quản lý độ phức tạp.

OOP đưa ra một cách tiếp cận khác.

Thay vì xem dữ liệu và các hàm xử lý là những thành phần riêng biệt, chúng ta nhóm chúng lại thành những đối tượng có trạng thái và hành vi.

Ví dụ:

```csharp
public class Employee
{
    public string Name { get; set; }

    public int Age { get; set; }

    public decimal Salary { get; set; }

    public decimal CalculateSalary()
    {
        return Salary;
    }
}
```

Bây giờ, chúng ta có thể tạo nhiều đối tượng Employee:

```csharp
var employee1 = new Employee
{
    Name = "John",
    Age = 30,
    Salary = 20000000
};

var employee2 = new Employee
{
    Name = "David",
    Age = 35,
    Salary = 25000000
};
```

Mỗi đối tượng có dữ liệu riêng nhưng cùng chia sẻ một cấu trúc và hành vi được định nghĩa bởi Employee.

Đây chính là một trong những tư tưởng quan trọng nhất của OOP:

**Tổ chức chương trình xoay quanh các đối tượng, trong đó dữ liệu và hành vi liên quan được đặt cùng nhau.**

## 2. Class và Object – Hai khái niệm nền tảng

Trước khi tìm hiểu sâu hơn về OOP, chúng ta cần phân biệt hai khái niệm thường xuyên xuất hiện: Class và Object.

### Class – Bản thiết kế

Class là một định nghĩa mô tả cấu trúc và hành vi mà các đối tượng thuộc class đó có thể có.

Ví dụ, chúng ta định nghĩa một class Car:

```csharp
public class Car
{
    public string Brand { get; set; }

    public string Model { get; set; }

    public void Start()
    {
        Console.WriteLine("Car started");
    }

    public void Stop()
    {
        Console.WriteLine("Car stopped");
    }
}
```

Class Car mô tả một chiếc xe có thương hiệu, model và hai hành vi Start, Stop.

Tuy nhiên, bản thân class Car không đại diện cho một chiếc xe cụ thể.

### Object – Đối tượng thực tế

Object là một thể hiện (instance) được tạo ra từ class.

```csharp
var car1 = new Car
{
    Brand = "Toyota",
    Model = "Camry"
};

var car2 = new Car
{
    Brand = "Honda",
    Model = "Civic"
};
```

Ở đây:

- Car là Class.
- car1 và car2 là hai Object khác nhau.
- Mỗi Object có trạng thái riêng.
- Cả hai đều có thể sử dụng những hành vi được định nghĩa trong Car.

Có thể hình dung Class giống như bản thiết kế của một ngôi nhà, còn Object là những ngôi nhà thực tế được xây dựng từ bản thiết kế đó.

### Một số khái niệm liên quan

Trong quá trình làm việc với Class và Object, bạn sẽ thường gặp:

**Field:** Biến được khai báo bên trong class để lưu trữ trạng thái.

**Property:** Thành phần cung cấp cơ chế truy cập và kiểm soát dữ liệu của đối tượng.

**Method:** Hàm mô tả hành vi của đối tượng.

**Constructor:** Phương thức đặc biệt được gọi khi tạo một instance, thường dùng để khởi tạo trạng thái ban đầu.

**Access Modifier:** Quy định phạm vi truy cập của các thành phần như public, private, protected và internal.

Ví dụ:

```csharp
public class BankAccount
{
    private decimal _balance;

    public string AccountNumber { get; private set; }

    public BankAccount(string accountNumber, decimal initialBalance)
    {
        AccountNumber = accountNumber;
        _balance = initialBalance;
    }

    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Amount must be positive");

        _balance += amount;
    }

    public decimal GetBalance()
    {
        return _balance;
    }
}
```

Ở ví dụ này, chúng ta không cho phép bên ngoài thay đổi trực tiếp số dư tài khoản. Việc thay đổi số dư phải thông qua các hành vi được cung cấp bởi BankAccount.

Đây chính là điểm bắt đầu để hiểu về tính đóng gói.

## 3. Bốn tính chất cơ bản của OOP

OOP thường được giới thiệu thông qua bốn tính chất: Encapsulation, Inheritance, Polymorphism và Abstraction.

Đây không chỉ là bốn khái niệm cần ghi nhớ khi phỏng vấn. Chúng là những công cụ tư duy giúp chúng ta thiết kế và tổ chức phần mềm.

### 3.1. Encapsulation – Tính đóng gói

Hãy quay lại ví dụ BankAccount.

Một tài khoản ngân hàng có số dư. Nếu bất kỳ thành phần nào trong chương trình cũng có thể thay đổi số dư, chúng ta sẽ gặp vấn đề.

Ví dụ:

```csharp
public class BankAccount
{
    public decimal Balance { get; set; }
}
```

Với thiết kế này, bất kỳ đoạn code nào cũng có thể thực hiện:

```csharp
account.Balance = -100000000;
```

Rõ ràng, đây không phải là trạng thái hợp lệ của một tài khoản ngân hàng.

Chúng ta cần kiểm soát cách dữ liệu được truy cập và thay đổi.

```csharp
public class BankAccount
{
    private decimal _balance;

    public decimal Balance => _balance;

    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Invalid amount");

        _balance += amount;
    }

    public void Withdraw(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Invalid amount");

        if (amount > _balance)
            throw new InvalidOperationException("Insufficient balance");

        _balance -= amount;
    }
}
```

Bây giờ, bên ngoài không thể trực tiếp thay đổi số dư.

Mọi thao tác đều phải thông qua Deposit hoặc Withdraw.

Điều này giúp đối tượng tự bảo vệ trạng thái của nó và đảm bảo các quy tắc nghiệp vụ được thực thi nhất quán.

Đó là bản chất của Encapsulation.

**Encapsulation không đơn giản chỉ là khai báo private và public. Nó là việc kiểm soát quyền truy cập và bảo vệ tính hợp lệ của trạng thái đối tượng.**

### 3.2. Inheritance – Tính kế thừa

Trong thực tế, nhiều đối tượng có những đặc điểm và hành vi chung.

Ví dụ, trong một hệ thống quản lý nhân sự, chúng ta có:

- FullTimeEmployee.
- PartTimeEmployee.
- ContractEmployee.

Tất cả đều là nhân viên và có những thông tin chung như Name, EmployeeCode, Department.

Nếu mỗi class tự định nghĩa lại những thuộc tính này, chúng ta sẽ có rất nhiều code trùng lặp.

Inheritance cho phép một class kế thừa những đặc điểm và hành vi từ một class khác.

```csharp
public class Employee
{
    public string Name { get; set; }

    public string EmployeeCode { get; set; }

    public virtual decimal CalculateSalary()
    {
        return 0;
    }
}
```

Class FullTimeEmployee có thể kế thừa Employee:

```csharp
public class FullTimeEmployee : Employee
{
    public decimal MonthlySalary { get; set; }

    public override decimal CalculateSalary()
    {
        return MonthlySalary;
    }
}
```

Trong khi đó, PartTimeEmployee có cách tính lương khác:

```csharp
public class PartTimeEmployee : Employee
{
    public decimal HourlyRate { get; set; }

    public int WorkingHours { get; set; }

    public override decimal CalculateSalary()
    {
        return HourlyRate * WorkingHours;
    }
}
```

Nhờ kế thừa, chúng ta có thể tái sử dụng những thành phần chung và mở rộng hành vi theo nhu cầu.

Tuy nhiên, có một điều cần lưu ý:

**Không phải cứ có những thuộc tính giống nhau thì chúng ta nên sử dụng Inheritance.**

Kế thừa nên phản ánh mối quan hệ IS-A.

Ví dụ:

- FullTimeEmployee IS-A Employee.
- PartTimeEmployee IS-A Employee.

Nếu hai class chỉ tình cờ có một số thuộc tính giống nhau, việc sử dụng kế thừa có thể tạo ra những mối quan hệ không hợp lý.

Trong nhiều trường hợp, Composition sẽ là lựa chọn tốt hơn.

### 3.3. Polymorphism – Tính đa hình

Polymorphism có nghĩa là đa hình, cho phép chúng ta làm việc với nhiều đối tượng khác nhau thông qua một kiểu chung, nhưng mỗi đối tượng có thể thực hiện hành vi theo cách riêng.

Tiếp tục ví dụ Employee.

Chúng ta có hai loại nhân viên với cách tính lương khác nhau:

```csharp
Employee employee1 = new FullTimeEmployee
{
    Name = "John",
    MonthlySalary = 20000000
};

Employee employee2 = new PartTimeEmployee
{
    Name = "David",
    HourlyRate = 100000,
    WorkingHours = 100
};
```

Mặc dù cả hai đều được tham chiếu thông qua kiểu Employee, khi gọi CalculateSalary(), chương trình sẽ thực thi phiên bản tương ứng với kiểu đối tượng thực tế.

```csharp
var employees = new List<Employee>
{
    employee1,
    employee2
};

foreach (var employee in employees)
{
    Console.WriteLine(employee.CalculateSalary());
}
```

Chúng ta không cần viết:

```csharp
if (employee is FullTimeEmployee)
{
    // Calculate full-time salary
}
else if (employee is PartTimeEmployee)
{
    // Calculate part-time salary
}
```

Thay vào đó, mỗi class tự chịu trách nhiệm triển khai hành vi của mình.

Đây chính là một trong những lợi ích lớn nhất của Polymorphism: giảm sự phụ thuộc vào các loại đối tượng cụ thể.

Trong C#, đa hình thường được thể hiện thông qua:

- Method Overriding: Ghi đè phương thức từ lớp cha.
- Method Overloading: Nhiều phương thức cùng tên nhưng khác danh sách tham số.
- Interface: Các đối tượng khác nhau triển khai cùng một hợp đồng hành vi.

Lưu ý: Overloading thường được gọi là đa hình lúc biên dịch (compile-time polymorphism), còn overriding thông qua virtual/override là đa hình lúc chạy (runtime polymorphism).

### 3.4. Abstraction – Tính trừu tượng

Hãy tưởng tượng bạn sử dụng một chiếc máy ATM.

Bạn có thể thực hiện các thao tác:

- Rút tiền.
- Chuyển khoản.
- Kiểm tra số dư.

Bạn không cần biết bên trong máy ATM giao tiếp với ngân hàng như thế nào, truy vấn database ra sao hoặc xử lý giao dịch như thế nào.

Bạn chỉ cần biết những thao tác được cung cấp và cách sử dụng chúng.

Đây là tư tưởng của Abstraction.

Trong lập trình, Abstraction cho phép chúng ta chỉ thể hiện những hành vi cần thiết và che giấu các chi tiết triển khai bên trong.

Trong C#, chúng ta thường sử dụng Interface hoặc Abstract Class để xây dựng abstraction.

Ví dụ:

```csharp
public interface IPaymentService
{
    Task<bool> PayAsync(decimal amount);
}
```

Chúng ta có thể có nhiều cách triển khai:

```csharp
public class CreditCardPaymentService : IPaymentService
{
    public async Task<bool> PayAsync(decimal amount)
    {
        // Process credit card payment
        return true;
    }
}
```

```csharp
public class BankTransferPaymentService : IPaymentService
{
    public async Task<bool> PayAsync(decimal amount)
    {
        // Process bank transfer
        return true;
    }
}
```

Thành phần sử dụng dịch vụ thanh toán chỉ cần làm việc với IPaymentService.

```csharp
public class OrderService
{
    private readonly IPaymentService _paymentService;

    public OrderService(IPaymentService paymentService)
    {
        _paymentService = paymentService;
    }

    public async Task CheckoutAsync(decimal amount)
    {
        await _paymentService.PayAsync(amount);
    }
}
```

OrderService không cần biết thanh toán được thực hiện bằng thẻ tín dụng hay chuyển khoản.

Nó chỉ cần biết rằng đối tượng được cung cấp có khả năng thực hiện thanh toán.

Đây cũng là một trong những nền tảng quan trọng của Dependency Inversion Principle và Dependency Injection.

## 4. Composition – Một tư duy quan trọng bên cạnh Inheritance

Khi mới học OOP, chúng ta thường tập trung rất nhiều vào Inheritance.

Tuy nhiên, trong các hệ thống phần mềm thực tế, Composition cũng là một kỹ thuật thiết kế rất quan trọng.

Hãy xem xét một ví dụ:

Một chiếc xe có động cơ, hệ thống phanh và hệ thống điều hòa.

Chúng ta không thể nói:

- Car IS-A Engine.
- Car IS-A BrakeSystem.

Nhưng chúng ta có thể nói:

- Car HAS-A Engine.
- Car HAS-A BrakeSystem.

Đây là mối quan hệ HAS-A, thường được mô hình hóa bằng Composition.

```csharp
public class Engine
{
    public void Start()
    {
        Console.WriteLine("Engine started");
    }
}
```

```csharp
public class BrakeSystem
{
    public void Apply()
    {
        Console.WriteLine("Braking...");
    }
}
```

```csharp
public class Car
{
    private readonly Engine _engine;
    private readonly BrakeSystem _brakeSystem;

    public Car(Engine engine, BrakeSystem brakeSystem)
    {
        _engine = engine;
        _brakeSystem = brakeSystem;
    }

    public void Start()
    {
        _engine.Start();
    }

    public void Brake()
    {
        _brakeSystem.Apply();
    }
}
```

Car không cần kế thừa Engine hay BrakeSystem.

Nó sử dụng những đối tượng này như các thành phần cấu thành nên chính nó.

Composition mang lại một số lợi ích:

- Giảm sự phụ thuộc vào cấu trúc kế thừa.
- Dễ dàng thay thế các thành phần.
- Tăng khả năng tái sử dụng.
- Dễ kiểm thử thông qua việc thay thế dependency.

Đây cũng là lý do chúng ta thường nghe đến nguyên tắc:

**Favor Composition over Inheritance.**

Điều này không có nghĩa là không nên sử dụng kế thừa, mà là không nên lạm dụng kế thừa khi Composition giải quyết vấn đề tốt hơn.

## 5. Interface và Abstract Class – Khi nào nên sử dụng?

Đây là một trong những chủ đề thường gặp trong phỏng vấn C#.

Cả Interface và Abstract Class đều có thể được sử dụng để xây dựng abstraction, nhưng chúng có mục đích và đặc điểm khác nhau.

### Interface

Interface mô tả một hợp đồng (contract) mà các class triển khai phải đáp ứng.

Ví dụ:

```csharp
public interface INotificationService
{
    Task SendAsync(string message);
}
```

Các class khác nhau có thể triển khai interface này:

```csharp
public class EmailNotificationService : INotificationService
{
    public Task SendAsync(string message)
    {
        // Send email
        return Task.CompletedTask;
    }
}
```

```csharp
public class SmsNotificationService : INotificationService
{
    public Task SendAsync(string message)
    {
        // Send SMS
        return Task.CompletedTask;
    }
}
```

Một class có thể triển khai nhiều interface.

Interface phù hợp khi chúng ta muốn định nghĩa một hợp đồng hành vi mà nhiều thành phần khác nhau có thể thực hiện.

### Abstract Class

Abstract Class là một class không thể tạo instance trực tiếp.

Nó có thể chứa:

- Field.
- Property.
- Constructor.
- Method có triển khai sẵn.
- Abstract Method yêu cầu class con triển khai.

Ví dụ:

```csharp
public abstract class NotificationService
{
    protected string ApplicationName { get; }

    protected NotificationService(string applicationName)
    {
        ApplicationName = applicationName;
    }

    public void Log(string message)
    {
        Console.WriteLine($"{ApplicationName}: {message}");
    }

    public abstract Task SendAsync(string message);
}
```

Các class kế thừa có thể sử dụng logic chung và triển khai hành vi riêng.

### So sánh

| Tiêu chí | Interface | Abstract Class |
|---|---|---|
| Mục đích | Định nghĩa contract | Chia sẻ abstraction và implementation |
| Constructor | Không có instance constructor | Có |
| Field instance | Không | Có |
| Implementation | Có thể có default implementation | Có |
| Kế thừa | Có thể triển khai nhiều interface | Chỉ kế thừa một class |
| State | Không có instance state | Có thể quản lý state |

Trong C# hiện đại, Interface cũng hỗ trợ default interface methods và một số thành viên có implementation. Vì vậy, không nên hiểu Interface chỉ đơn giản là tập hợp các phương thức abstract như cách giải thích truyền thống.

Một cách lựa chọn thực tế:

- Dùng Interface khi muốn định nghĩa một khả năng hoặc hợp đồng.
- Dùng Abstract Class khi nhiều class có chung trạng thái hoặc logic cần tái sử dụng.

## 6. Access Modifiers – Kiểm soát phạm vi truy cập

Một phần quan trọng của OOP là khả năng kiểm soát việc truy cập các thành phần bên trong class.

C# cung cấp các access modifier phổ biến:

| Modifier | Phạm vi truy cập |
|---|---|
| public | Bất kỳ thành phần nào có thể truy cập |
| private | Chỉ bên trong kiểu khai báo |
| protected | Bên trong kiểu khai báo và các lớp kế thừa |
| internal | Trong cùng assembly |
| protected internal | Cùng assembly hoặc lớp kế thừa |
| private protected | Trong cùng assembly và lớp kế thừa |

Việc lựa chọn access modifier không chỉ ảnh hưởng đến khả năng truy cập mà còn ảnh hưởng đến mức độ phụ thuộc giữa các thành phần.

Một nguyên tắc thiết kế hữu ích:

**Chỉ công khai những gì thực sự cần thiết. Giữ các chi tiết triển khai ở phạm vi truy cập nhỏ nhất phù hợp.**

Điều này giúp giảm bề mặt API và hạn chế việc các thành phần khác phụ thuộc vào chi tiết nội bộ.

## 7. OOP trong một hệ thống thực tế

Đến đây, chúng ta đã tìm hiểu các khái niệm cơ bản.

Nhưng làm thế nào để áp dụng chúng trong một hệ thống thực tế?

Hãy lấy ví dụ xây dựng một hệ thống bán hàng.

Một đơn hàng có thể bao gồm:

- Order.
- OrderItem.
- Customer.
- Payment.
- Product.

Chúng ta có thể bắt đầu bằng cách mô hình hóa các đối tượng.

```csharp
public class Order
{
    private readonly List<OrderItem> _items = new();

    public Guid Id { get; private set; }

    public IReadOnlyCollection<OrderItem> Items => _items.AsReadOnly();

    public decimal TotalAmount =>
        _items.Sum(x => x.Quantity * x.UnitPrice);

    public void AddItem(Product product, int quantity)
    {
        if (quantity <= 0)
            throw new ArgumentException("Invalid quantity");

        var item = new OrderItem(product.Id, quantity, product.Price);

        _items.Add(item);
    }
}
```

```csharp
public class OrderItem
{
    public Guid ProductId { get; }

    public int Quantity { get; }

    public decimal UnitPrice { get; }

    public OrderItem(Guid productId, int quantity, decimal unitPrice)
    {
        ProductId = productId;
        Quantity = quantity;
        UnitPrice = unitPrice;
    }
}
```

Trong ví dụ này, chúng ta đã áp dụng một số tư tưởng:

- Encapsulation: Danh sách Items không cho phép bên ngoài thay đổi trực tiếp.
- Abstraction: Người sử dụng Order chỉ cần gọi AddItem.
- Composition: Order chứa và quản lý các OrderItem.
- Business Rules: Số lượng sản phẩm phải lớn hơn 0.
- Single Responsibility: Order tập trung quản lý trạng thái và hành vi của đơn hàng.

Tuy nhiên, đây mới là một ví dụ đơn giản.

Trong một hệ thống thực tế, chúng ta còn cần xem xét các vấn đề như:

- Một sản phẩm có thể thay đổi giá sau khi đơn hàng được tạo.
- Đơn hàng cần lưu lại giá tại thời điểm mua.
- Không thể thêm sản phẩm khi đơn hàng đã hoàn tất.
- Đơn hàng cần có trạng thái và quy tắc chuyển trạng thái.
- Thanh toán phải được thực hiện thông qua một dịch vụ riêng.
- Dữ liệu cần được lưu trữ và đảm bảo tính nhất quán.

Đây chính là lúc OOP bắt đầu kết hợp với các nguyên tắc SOLID, Design Patterns và Domain-Driven Design để giải quyết những bài toán phức tạp hơn.

## 8. Những sai lầm thường gặp khi học và áp dụng OOP

Biết định nghĩa không có nghĩa là chúng ta đã hiểu OOP.

Trong quá trình phát triển phần mềm, có một số sai lầm rất phổ biến.

**1. Lạm dụng Inheritance**

Tạo ra quá nhiều lớp cha và lớp con chỉ để tái sử dụng code.

Điều này khiến hệ thống có cấu trúc kế thừa phức tạp và khó thay đổi.

**2. Class chỉ chứa dữ liệu**

Một số class chỉ có property và không có bất kỳ hành vi nào.

Điều này không nhất thiết là sai, vì DTO và một số mô hình dữ liệu có mục đích riêng. Nhưng nếu mọi class nghiệp vụ đều chỉ chứa dữ liệu, logic sẽ bị phân tán ra bên ngoài.

**3. God Object**

Một class chịu trách nhiệm quá nhiều thứ: quản lý dữ liệu, xử lý nghiệp vụ, gửi email, ghi log, truy cập database...

Đây là dấu hiệu của thiết kế thiếu phân chia trách nhiệm.

**4. Lạm dụng Abstraction**

Không phải class nào cũng cần Interface.

Việc tạo interface cho mọi class mà không có lý do thiết kế rõ ràng có thể khiến code phức tạp hơn và khó theo dõi hơn.

**5. Nhầm lẫn giữa OOP và việc sử dụng Class**

Việc tạo ra hàng trăm class không có nghĩa là chúng ta đang thiết kế OOP tốt.

OOP là tư duy tổ chức và quản lý trạng thái, hành vi, mối quan hệ và sự phụ thuộc giữa các đối tượng.

## 9. Kết luận – OOP không chỉ là bốn tính chất

Khi bắt đầu học OOP, chúng ta thường được giới thiệu bốn tính chất: Encapsulation, Inheritance, Polymorphism và Abstraction.

Đây là những nền tảng quan trọng, nhưng hiểu OOP không chỉ dừng lại ở việc nhớ định nghĩa hoặc biết viết một class.

Điều quan trọng hơn là hiểu cách sử dụng những khái niệm này để giải quyết các vấn đề thực tế:

- Làm thế nào để bảo vệ trạng thái của một đối tượng?
- Làm thế nào để giảm sự trùng lặp code?
- Làm thế nào để các thành phần có thể thay thế lẫn nhau?
- Làm thế nào để giảm sự phụ thuộc giữa các module?
- Làm thế nào để thay đổi một chức năng mà không ảnh hưởng đến toàn bộ hệ thống?

OOP giúp chúng ta có một cách tư duy để tổ chức phần mềm. Nhưng để xây dựng những hệ thống thực sự tốt, chúng ta cần tiến xa hơn với SOLID, Design Patterns, Clean Code và Software Architecture.

**Một Developer giỏi không phải là người tạo ra nhiều class nhất, mà là người biết cách tổ chức các thành phần sao cho hệ thống dễ hiểu, dễ thay đổi và có thể phát triển theo thời gian.**