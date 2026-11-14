Programming Fundamentals – Tư duy lập trình.

# Quay lại những nền tảng của lập trình: OOP, SOLID và những điều một Developer cần hiểu

Nếu bạn dạo qua một vòng các tin tuyển dụng lập trình, bạn sẽ thường bắt gặp những yêu cầu như:

> Strong understanding of OOP, SOLID principles, collections, exception handling, and LINQ.

Đây gần như là những yêu cầu cơ bản đối với một lập trình viên .NET. Nhưng đã bao giờ bạn tự hỏi tại sao chúng ta phải học những kiến thức này? Chúng giải quyết vấn đề gì và tại sao chúng lại quan trọng đến vậy?

Vậy thì hãy cùng quay lại những nền tảng của lập trình.

## 1. Từ lập trình tuần tự đến lập trình hướng đối tượng

Pascal là một đại diện tiêu biểu cho ngôn ngữ lập trình thủ tục (Procedural Programming).

Ở cách tiếp cận này, chương trình được xây dựng từ các câu lệnh, hàm và thủ tục. Các câu lệnh được thực thi theo một luồng điều khiển, thường là từ trên xuống dưới, kết hợp với các cấu trúc điều kiện và vòng lặp.

Khi bài toán còn đơn giản, cách tiếp cận này hoạt động rất hiệu quả.

Tuy nhiên, khi bài toán trở nên phức tạp, số lượng chức năng tăng lên, dữ liệu cần quản lý nhiều hơn và các chức năng bắt đầu phụ thuộc lẫn nhau, code cũng trở nên phức tạp.

Chúng ta bắt đầu gặp những vấn đề:

- Một dữ liệu được sử dụng và thay đổi ở nhiều nơi.
- Các hàm có mối liên hệ chặt chẽ với nhau.
- Việc sửa đổi một chức năng có thể ảnh hưởng đến nhiều chức năng khác.
- Khó tái sử dụng code.
- Khó bảo trì và mở rộng hệ thống.

Nói cách khác, vấn đề không còn nằm ở việc chúng ta có thể viết được chương trình hay không, mà là làm thế nào để quản lý độ phức tạp của chương trình.

Đó là lúc tư duy lập trình hướng đối tượng (Object-Oriented Programming - OOP) trở nên quan trọng.

C++ là một trong những ngôn ngữ phổ biến hỗ trợ mạnh mẽ lập trình hướng đối tượng. Tuy nhiên, OOP đã xuất hiện trước đó, tiêu biểu là từ Simula và Smalltalk.

Thay vì chỉ tập trung vào các câu lệnh và hàm để xử lý dữ liệu, OOP đưa ra một cách tổ chức chương trình dựa trên các đối tượng.

Một đối tượng có thể chứa:
- **State:** Trạng thái, dữ liệu mà đối tượng quản lý.
- **Behavior:** Hành vi, những gì đối tượng có thể thực hiện.

Ví dụ, khi xây dựng một hệ thống quản lý nhân viên, thay vì tạo ra nhiều biến và hàm rời rạc như EmployeeName, EmployeeSalary, CalculateSalary(), chúng ta có thể tổ chức chúng thành một đối tượng Employee.

Từ đó, chúng ta có bốn khái niệm nền tảng:

- **Encapsulation (Tính đóng gói):** Bảo vệ dữ liệu và kiểm soát cách dữ liệu được truy cập, thay đổi.
- **Inheritance (Tính kế thừa):** Cho phép một lớp kế thừa và mở rộng đặc điểm của lớp khác.
- **Polymorphism (Tính đa hình):** Cho phép các đối tượng khác nhau phản hồi cùng một lời gọi theo những cách khác nhau.
- **Abstraction (Tính trừu tượng):** Che giấu chi tiết triển khai và chỉ thể hiện những gì cần thiết.

OOP giúp chúng ta tổ chức code tốt hơn, mô hình hóa các thành phần trong bài toán thực tế và tạo ra khả năng mở rộng.

Tuy nhiên, OOP không phải là giải pháp cho tất cả mọi vấn đề.

Nếu không có cách tổ chức hợp lý, một hệ thống OOP vẫn có thể trở thành một mớ code phức tạp với hàng trăm class, các mối quan hệ phụ thuộc chồng chéo và rất khó thay đổi.

Vì vậy, chúng ta cần những nguyên tắc thiết kế tốt hơn.

## 2. SOLID – Làm thế nào để viết code hướng đối tượng tốt?

Khi đã biết cách tổ chức chương trình bằng Class và Object, câu hỏi tiếp theo là:

Làm thế nào để thiết kế các class sao cho dễ bảo trì, dễ mở rộng và ít gây ảnh hưởng đến những thành phần khác?

Đây là lúc chúng ta cần đến SOLID.

SOLID là tập hợp năm nguyên tắc thiết kế hướng đối tượng:

**S – Single Responsibility Principle**

Một class nên có một trách nhiệm chính, hay chính xác hơn là một lý do để thay đổi.

Ví dụ, một class EmployeeService không nên vừa xử lý nghiệp vụ nhân viên, vừa gửi email, vừa ghi log, vừa thực hiện thao tác lưu file.

Chúng ta nên phân chia các trách nhiệm này thành những thành phần phù hợp.

**O – Open/Closed Principle**

Một thành phần nên mở để mở rộng nhưng đóng đối với việc sửa đổi.

Khi cần bổ sung chức năng mới, chúng ta nên ưu tiên mở rộng hành vi thông qua abstraction thay vì liên tục sửa đổi logic hiện có.

**L – Liskov Substitution Principle**

Một đối tượng của lớp con phải có thể thay thế đối tượng của lớp cha mà không làm sai lệch tính đúng đắn của chương trình.

Nói cách khác, kế thừa không chỉ là việc chia sẻ code mà còn phải đảm bảo tính tương thích về hành vi.

**I – Interface Segregation Principle**

Không nên ép một class phải triển khai những phương thức mà nó không cần sử dụng.

Thay vì một interface quá lớn, hãy chia thành những interface nhỏ, tập trung vào từng nhóm hành vi.

**D – Dependency Inversion Principle**

Các module cấp cao không nên phụ thuộc trực tiếp vào các module cấp thấp. Cả hai nên phụ thuộc vào abstraction.

Đây cũng là một trong những nền tảng quan trọng để xây dựng Dependency Injection và các kiến trúc như Clean Architecture.

SOLID không phải là những quy tắc bắt buộc phải áp dụng máy móc trong mọi tình huống.

Điều quan trọng là hiểu vấn đề mà mỗi nguyên tắc muốn giải quyết và biết khi nào nên áp dụng chúng.

## 3. Collections – Quản lý và tổ chức dữ liệu

Trong một chương trình thực tế, chúng ta hiếm khi chỉ làm việc với một đối tượng đơn lẻ.

Hãy tưởng tượng bạn đang xây dựng hệ thống quản lý nhân viên.

Bạn cần lưu trữ danh sách nhân viên, tìm kiếm một nhân viên theo ID, sắp xếp theo lương hoặc lọc những nhân viên thuộc một phòng ban.

Nếu chỉ sử dụng các biến đơn lẻ, việc quản lý dữ liệu sẽ nhanh chóng trở nên khó khăn.

Đó là lý do chúng ta cần Collections.

Trong C#, Collections cung cấp các cấu trúc dữ liệu giúp lưu trữ và thao tác với nhiều phần tử.

Một số cấu trúc phổ biến:

- **Array:** Mảng có kích thước cố định.
- **List<T>:** Danh sách có khả năng thay đổi kích thước.
- **Dictionary<TKey, TValue>:** Lưu trữ dữ liệu theo cặp key-value, hỗ trợ tra cứu theo khóa.
- **HashSet<T>:** Lưu trữ các phần tử duy nhất.
- **Queue<T>:** Cấu trúc dữ liệu hàng đợi FIFO.
- **Stack<T>:** Cấu trúc dữ liệu ngăn xếp LIFO.

Tuy nhiên, hiểu Collections không chỉ dừng lại ở việc biết sử dụng List hay Dictionary.

Một Developer cần hiểu cách các cấu trúc dữ liệu hoạt động, ưu nhược điểm của chúng và lựa chọn cấu trúc phù hợp với bài toán.

Ví dụ:

- Khi cần truy cập phần tử theo index: Array hoặc List.
- Khi cần tìm kiếm theo key: Dictionary.
- Khi cần đảm bảo không có phần tử trùng lặp: HashSet.
- Khi cần xử lý tác vụ theo thứ tự đến trước: Queue.

Đặc biệt, cần hiểu thêm về Big O Notation, Time Complexity và Space Complexity để đánh giá hiệu năng của các thao tác trên dữ liệu.

## 4. Exception Handling – Kiểm soát những tình huống bất thường

Một chương trình không phải lúc nào cũng chạy trong điều kiện lý tưởng.

Người dùng có thể nhập dữ liệu không hợp lệ, kết nối database có thể bị gián đoạn, API bên ngoài có thể không phản hồi hoặc một file mà chương trình cần sử dụng không tồn tại.

Đây là những tình huống mà chúng ta cần xử lý thay vì để chương trình dừng đột ngột.

Exception Handling là cơ chế giúp chương trình nhận biết và kiểm soát những tình huống bất thường trong quá trình thực thi.

Trong C#, chúng ta thường sử dụng:

- **try:** Đặt đoạn code có khả năng phát sinh exception.
- **catch:** Bắt và xử lý exception.
- **finally:** Thực hiện những thao tác cần được đảm bảo chạy sau quá trình xử lý.
- **throw:** Chủ động phát sinh hoặc ném lại exception.

Tuy nhiên, viết Exception Handling tốt không đơn giản là đặt try-catch ở mọi nơi.

Một Developer cần hiểu:

- Phân biệt Exception và những kết quả nghiệp vụ thông thường.
- Khi nào nên bắt exception và khi nào nên để exception lan truyền lên tầng xử lý phù hợp.
- Không nuốt exception một cách im lặng.
- Log đầy đủ thông tin cần thiết để phục vụ việc điều tra lỗi.
- Quản lý tài nguyên đúng cách thông qua IDisposable và using.
- Thiết kế custom exception khi thực sự cần thiết.

Mục tiêu không phải là làm cho chương trình không bao giờ phát sinh lỗi, mà là đảm bảo hệ thống có thể phản ứng một cách an toàn, có kiểm soát và dễ dàng truy vết khi xảy ra lỗi.

## 5. LINQ – Làm việc với dữ liệu theo một cách biểu đạt hơn

Sau khi biết cách tổ chức đối tượng và lưu trữ dữ liệu bằng Collections, chúng ta sẽ gặp một nhu cầu rất phổ biến: truy vấn và xử lý dữ liệu.

Ví dụ, chúng ta có một danh sách nhân viên và muốn tìm những người có mức lương trên 20 triệu, sắp xếp theo tên và chỉ lấy 10 người đầu tiên.

Nếu sử dụng vòng lặp thông thường, chúng ta phải tự viết logic lọc, sắp xếp và giới hạn kết quả.

LINQ (Language Integrated Query) được giới thiệu trong .NET 3.5, giúp tích hợp khả năng truy vấn dữ liệu trực tiếp vào ngôn ngữ C#.

Thay vì phải viết nhiều đoạn code xử lý thủ công, chúng ta có thể biểu đạt ý định một cách rõ ràng hơn.

Ví dụ:

```csharp
var result = employees
    .Where(x => x.Salary > 20_000_000)
    .OrderBy(x => x.Name)
    .Take(10)
    .ToList();
```

LINQ không chỉ làm việc với List hay Array mà còn có thể làm việc với nhiều nguồn dữ liệu khác nhau thông qua các provider.

Hai khái niệm quan trọng cần hiểu:

- **LINQ to Objects:** Truy vấn các collection trong bộ nhớ.
- **LINQ to Entities:** Truy vấn dữ liệu thông qua Entity Framework, thường được chuyển đổi thành SQL để thực thi trên database.

Một Developer cần hiểu thêm về:

- Method Syntax và Query Syntax.
- Deferred Execution và Immediate Execution.
- IEnumerable và IQueryable.
- Select, SelectMany, Where, GroupBy, Join.
- Sự khác biệt giữa truy vấn trên bộ nhớ và truy vấn database.
- Những vấn đề hiệu năng như N+1 Query và truy vấn không được tối ưu.

LINQ giúp code ngắn gọn hơn, nhưng nếu không hiểu cách nó thực thi, chúng ta hoàn toàn có thể viết ra những truy vấn có hiệu năng rất kém.

## 6. Những kiến thức này liên kết với nhau như thế nào?

Đến đây, chúng ta có thể nhìn thấy một bức tranh tổng thể.

Những kiến thức thường xuất hiện trong yêu cầu tuyển dụng không phải là các khái niệm độc lập, mà chúng bổ trợ cho nhau trong quá trình xây dựng phần mềm.

- OOP giúp chúng ta tổ chức chương trình thành các đối tượng.
- SOLID giúp chúng ta thiết kế các đối tượng và mối quan hệ giữa chúng tốt hơn.
- Collections giúp chúng ta tổ chức và quản lý dữ liệu.
- LINQ giúp chúng ta truy vấn và xử lý dữ liệu hiệu quả hơn.
- Exception Handling giúp chúng ta kiểm soát các tình huống bất thường trong quá trình thực thi.

Khi kết hợp những kiến thức này, chúng ta có thể xây dựng những chương trình có cấu trúc rõ ràng, dễ bảo trì và có khả năng mở rộng.

Nhưng đây mới chỉ là nền tảng.

Trong một hệ thống thực tế, chúng ta còn phải giải quyết nhiều vấn đề lớn hơn: làm thế nào để tổ chức các module, quản lý sự phụ thuộc, giao tiếp giữa các thành phần, đảm bảo tính nhất quán của dữ liệu và duy trì hiệu năng khi số lượng người dùng tăng lên?

Đó là lúc chúng ta cần bước tiếp sang những kiến thức như Design Patterns, Software Architecture, Database Design, System Design và Distributed Systems.

**Lập trình không chỉ là biết sử dụng một ngôn ngữ hay framework. Đó là quá trình học cách tư duy, tổ chức và giải quyết những bài toán ngày càng phức tạp.**